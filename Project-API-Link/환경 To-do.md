1. base Entity -> enable (true, false), true default
	1. 삭제 시 enable->false
	2. 조회 시 조건, enable-= true 인것만
	3. 업데이트 시 enable=true 인것만 
	4. (수정 보류 - 도급시 필요)

2. 깃에서 소스 다운받은 후
	1. application.properties 를 만들어야 함. (로컬용)
	2. application-dev.properties 를 복사 하고, 명칭 변경
	3. database 변경하기
##### database  
spring.datasource.url=jdbc:h2:tcp://localhost/~/test;  
spring.datasource.driverClassName=org.h2.Driver  
spring.datasource.username=sa  
spring.datasource.password=  
spring.jpa.database-platform=org.hibernate.dialect.H2Dialect  
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.H2Dialect


3. 다음 위키 내용에 따라 포스트맨 설정 후, 테스트 진행
	1. [4.2.6 Interface - 3G연구소 - Eland WIKI](https://wiki.eland.co.kr/display/3glab/4.2.6+Interface)

4. 소스트리
	1. 사용전 feature 만들기
		1. deverlop branch 에서 pull 우선 받기
		2. 깃플로우 버튼 눌러서 "기능 만들기"
		3. stage 와 커밋으로 소스코드 보호
			1. 기능 마무리 전, develop 브랜치로 이동하여 pull 소스
		4. 마지막에 깃플로우 버튼 눌러서 "기능 마무리" -> develop branch 에 소스 전송


5. Inno-Frame 작업
	1. errordegtail => status->error
	2. data field 삭제
	3. 배포 : C:\Users\han.sungyoup01\.m2\settings.xml 확인 후 admin 추가.
	4. 이메일로 명령어 전달 받음.

6. Innolink-API 작업
	1. custom user - api
		1. custom_user, custom_attribute, custom_group 에 저장.
		2. 저장 시 결과 노출 (성공 리스트 및 실패 리스트)

krvaissodev02 서버 배포 설정
id: jenkins 
password: deploy+123 