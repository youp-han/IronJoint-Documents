1. Jenkins 에 Slack  플러그인 설치
	1. Jenkins 서버에 이 플러그인을 설치
	2. Jenkins 홈페이지에서 Manage Jenkins로 이동.
	3. Manage Plugins으로 이동합.
	4. 탭을 Available로 변경.
	5. "slack"을 검색.
	6. 설치할 항목 옆의 체크박스를 선택 및 설치

8. Slack 내 App 생성 및 WorkGroup 에 설치
9.  필요 시 Slack 계정을 생성: https://slack.com/
10. https://api.slack.com/apps로 이동하여 "Create New App"를 클릭.
11. "From an app manifest"를 클릭.
12. 워크스페이스를 선택.
13. Slack이 제공하는 예제 매니페스트를 삭제.
14. "YAML"을 클릭.
15. 다음 내용을 텍스트 상자에 복붙

bot 설정
```
display_information:
  name: Jenkins
features:
  bot_user:
    display_name: Jenkins사용자이름
    always_online: true
oauth_config:
  scopes:
    bot:
      - channels:read
      - chat:write
      - chat:write.customize
      - files:write
      - reactions:write
      - users:read
      - users:read.email
      - groups:read
settings:
  org_deploy_enabled: false
  socket_mode_enabled: false
  token_rotation_enabled: false
```


1. "Next"를 클릭.
2. "Create"를 클릭.
3. "Install App to Workspace"를 클릭.
4. "Allow"를 클릭.
5. 사이드바에서 "OAuth & Permissions"를 클릭.
6. "Bot User OAuth Access Token"을 복사.
7. Jenkins에서: "Manage Jenkins → System"에서 Slack 설정으로 이동.
8. Jenkins에서: "Add"를 클릭하여 새 "Secret text" 자격 증명을 생성하고 봇 사용자 토큰을 입력.
9. Jenkins에서: 드롭다운에서 새 "Secret text"를 선택.
10. Jenkins에서: 기본 채널을 추가
11. Jenkins에서: "Custom slack app bot user" 옵션을 선택.
12. 알림을 받으려는 Slack 채널에 Jenkins 봇 사용자를 초대.
13. Jenkins에서: "test connection"을 클릭. 기본 채널 / 기본 멤버에게 메시지가 전송되는지 확인.

pipeline 코드
```
slackSend color: "good", message: "Message from Jenkins Pipeline"
```

사용 예제
```
pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                timestamps {
                    echo "hello world"
                }
            }
        }
    }
    post {
        success {
            timestamps {
                echo "Sending Slack notification"
                slackSend(color: 'good', message: "Message from Jenkins Pipeline - ${currentBuild.fullDisplayName}")
            }
        }
    }
}
```