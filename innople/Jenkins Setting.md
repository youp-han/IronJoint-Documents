krvaissodev02 서버 배포 설정
id: jenkins 
password: deploy+123 

pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M3"
    }
    
    environment {
        SERVICE_NAME = 'keycloak'
        SOURCE_FILE = "${env.WORKSPACE}\\innopleauth\\target\\${params.JAR_FILE}" 
        TARGET_FOLDER = "${params.HOME_PATH}"
    }

    stages {
        stage('Modules checkout') {
            when {
                expression { params.ONLY_DEPLOY != 'true' }
            }
            steps {
                // Clone repository ABC into a subfolder named "ABC"
                checkout([$class: 'GitSCM', 
                          branches: [[name: '*/develop']], 
                          userRemoteConfigs: [[credentialsId: '4f302ace-ec4e-4c72-bbfb-edadd0b194a6', 
                            url: 'http://svn.elandsystems.com:8090/scm/git/2023/EIAMX']], 
                          extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'innopleauthmultimodule']]])
            }
        }
    
        stage('Application checkout') {
            when {
                expression { params.ONLY_DEPLOY != 'true' }
            }
            steps {
                // Clone repository ABC into a subfolder named "ABC"
                checkout([$class: 'GitSCM', 
                          branches: [[name: '*/develop']], 
                          userRemoteConfigs: [[credentialsId: '4f302ace-ec4e-4c72-bbfb-edadd0b194a6', 
                            url: 'http://svn.elandsystems.com:8090/scm/git/2023/EIAM']], 
                          extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'innopleauth']]])
            }
        }
        
        stage('Build') {
            when {
                expression { params.ONLY_DEPLOY != 'true' }
            }
            steps {
                // Run Maven on a Unix agent.
                // sh "mvn -Dmaven.test.failure.ignore=true clean package"
                dir('innopleauthmultimodule') {
                  // To run Maven on a Windows agent, use
                  bat "mvn -DskipTests clean package"
                }
            }
        }
        
        stage('Restart local service') {
            steps {
                script {
                    def scQuery = bat(script: "sc query %SERVICE_NAME% | find \"STATE\" | find /i \"RUNNING\" > nul", returnStatus: true)
                    if (scQuery == 0) {
                        //bat 'echo "Stop service %SERVICE_NAME%"'
                        bat 'sc stop %SERVICE_NAME%'
                    }
                }
                
                script {
                    def serviceName = "${env.SERVICE_NAME}" 
                    def timeoutSeconds = 120 // Maximum time to wait for service termination (adjust as needed)
                    def sleepSeconds = 10 // Time interval between status checks (adjust as needed)

                    def status
                    timeout(time: timeoutSeconds, unit: 'SECONDS') {
                        // Loop to check the service status until it is stopped or timeout occurs
                        while (true) {
                            // Execute the 'sc query' command to get the service status
                            def scQuery = bat(script: "sc query ${serviceName} | find \"STATE\" | find /i \"RUNNING\" > nul", returnStatus: true)

                            if (scQuery == 0) {
                                // Service is still running, wait and check again
                                sleep time: sleepSeconds, unit: 'SECONDS'
                            } else {
                                // Service is not found or stopped, break the loop
                                status = scQuery
                                break
                            }
                        }
                    }

                    if (status == 0) {
                        echo "Service '${serviceName}' did not terminate within the timeout period."
                    } else {
                        echo "Service '${serviceName}' has been successfully stopped."
                    }
                }
                
                script {
                    def oldJarPath = "${env.TARGET_FOLDER}${params.JAR_FILE}"
                    // Check if the old JAR file exists and delete it if present
                    if (fileExists(oldJarPath)) {
                        bat "DEL ${oldJarPath}"
                    }

                    // Copy the new JAR file to the target folder
                    bat "COPY /Y %SOURCE_FILE% %TARGET_FOLDER%"
                }
                
                bat "sc start %SERVICE_NAME%"
            }
        }
        
        stage('Restart remote service') {
            steps {
                script {
                
                    sshPublisher(publishers: [sshPublisherDesc(configName: 'krvaissodev04', transfers: [
                        sshTransfer(execCommand: ".\\App\\keycloak stop --no-elevate --force", execTimeout: 120000, flatten: false)
                    ], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
                    sshPublisher(publishers: [sshPublisherDesc(configName: 'krvaissodev04', transfers: [
                        sshTransfer(execCommand: "DEL .\\App\\${params.JAR_FILE}", execTimeout: 120000, flatten: false)
                    ], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
                    // Use the pre-configured SSH server configuration 'AppServer'
                    def remote = [:]
                    remote.name = 'krvaissodev04'
                    remote.sourceFiles = "innopleauth/target/${params.JAR_FILE}"  // Local file path
                    remote.removePrefix = "innopleauth/target"  // Remote directory where the file will be copied
                    remote.remoteDirectory = './App'  // Destination directory on the remote server

                    // Perform the file transfer
                    sshPublisher(publishers: [sshPublisherDesc(configName: remote.name, transfers: [remote], verbose: true)])
                    
                    sshPublisher(publishers: [sshPublisherDesc(configName: 'krvaissodev04', transfers: [
                        sshTransfer(execCommand: ".\\App\\keycloak start --no-elevate --force", execTimeout: 120000, flatten: false)
                    ], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)])
                }
            }
        }
    }
}
