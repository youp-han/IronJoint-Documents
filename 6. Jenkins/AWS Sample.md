AWS CodeDeploy Plugin Sample

```
pipeline {
    agent any
 
    tools {     
        maven 'Maven 3.6.3'
        jdk '1.8.0_60'  
    }
 
    environment {
        MAVEN_HOME = '/usr/local/apache-maven-3.6.3'
        WORKSPACE = "${env.WORKSPACE}" // Jenkins workspace
        AWS_REGION = 'ap-northeast-2'  // AWS CodeDeploy Region
        APPLICATION_NAME = '******'   // CodeDeploy Application Name
        DEPLOYMENT_GROUP_NAME = '********' // Deployment Group Name
        S3_BUCKET_NAME = '**********' // S3 Bucket Name for deployment
        DEPLOYMENT_CONFIG_NAME = 'CodeDeployDefault.AllAtOnce'  // Deployment config
        POLLING_TIMEOUT = 3000  // Polling Timeout in seconds
        POLLING_FREQUENCY = 15  // Polling Frequency in seconds
        SUBDIRECTORY = 'deploy_scripts/codedeploy'  // Subdirectory for deployment package
    }
 
 
    stages {
        stage('Checkout') {
            steps {
             
                checkout([
                    $class: 'SubversionSCM',
                    locations: [[
                        remote: "http://*****@${params.REV ?: 'HEAD'}",
                        credentialsId: '*****',
                        depthOption: 'infinity',
                        local: '*****',
                        ignoreExternalsOption: true
                    ]],
                    workspaceUpdater: [$class: 'CheckoutUpdater']
                ]) 
              
            }
        }
 
        stage('Build') {
            steps {
                dir('*****') { // '*****' 디렉토리에서 명령 실행
                    sh """
                    mvn clean versions:update-properties -Dspring.profiles.active=qas -Dmaven.test.skip=true -Pqas -U
                    mvn package -Dspring.profiles.active=qas -Dmaven.test.skip=true -Pqas -U
                    """
                }
            }
        }
 
        stage('Post-Build') {
            steps {
                dir('*****') { // '*****' 디렉토리로 이동
                    script {
                        // dist.zip 파일 복사
                        sh """
                        cp -rf "${WORKSPACE}/target/*****.zip" "${WORKSPACE}/${SUBDIRECTORY}/*****.zip"
                        """
                    }
                }
            }
        }
 
        stage('deploy') {
            steps{
                withCredentials([[$class:'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '*****',  secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                    step([$class: 'AWSCodeDeployPublisher',
                    applicationName: "${APPLICATION_NAME}",
                    awsAccessKey: AWS_ACCESS_KEY_ID,
                    awsSecretKey: AWS_SECRET_ACCESS_KEY,
                    credentials: 'awsAccessKey',
                    deploymentConfig: "${DEPLOYMENT_CONFIG_NAME}",
                    deploymentGroupAppspec: false,
                    deploymentGroupName: "${DEPLOYMENT_GROUP_NAME}",
                    excludes: '',
                    iamRoleArn: '',
                    includes: '**',
                    proxyHost: '',
                    proxyPort: 0,
                    region: "${AWS_REGION}",
                    s3bucket: "${S3_BUCKET_NAME}",
                    s3prefix: '',
                    subdirectory: "${SUBDIRECTORY}",
                    versionFileName: '',
                    waitForCompletion: true,
                    pollingTimeoutSec: 3000
                    ])
                }
          }
        }             
    }
 
    post {
        always {
            echo "Pipeline completed"
        }
        success {
            echo "Deployment succeeded"
        }
        failure {
            echo "Deployment failed"
        }
    }
}



