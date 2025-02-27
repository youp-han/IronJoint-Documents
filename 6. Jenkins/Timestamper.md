1. 젠킨스 배포 시 Console Output 에 시간 추가됨.
2. 젠킨스 플러그인 -  Timestamper 설치 필요 (Jenkins→Manage Jenkins->Plugin→Available plugins → (timestamper)
    
    ![](https://wiki.eland.co.kr/download/attachments/362417043/image2025-2-7_10-6-0.png?version=1&modificationDate=1738890361000&api=v2)
    
3. 사용의 예 
```
pipeline {
    agent any 
    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven 'Maven 3.6.3'
        jdk 'jdk1.8.0_92'
    }     
    environment {
        GITREPOSITORY = "http://git.repository.com/project"     
    } 
    stages {
        stage('Checkout') {
            steps {
                timestamps {
                    // Clone repository ABC into a subfolder named "ABC"
                    checkout([$class: 'GitSCM',
                              branches: [[name: '*/main']],
                              doGenerateSubmoduleConfigurations: false,
                              extensions: [],
                              userRemoteConfigs: [[credentialsId: 'ABCDEFG',
                                url: "${GITREPOSITORY}"]],
                              ])
                }
            }
        }     
        stage('Build') {
            steps {
                timestamps {
                    sh "mvn clean package -D maven.test.skip=true"
                }
            }
        }         
        stage('Deploy') {
            steps {
                timestamps {
					//Deploy script
                }
            }
        }
    } 
}
```