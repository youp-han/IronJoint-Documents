1. inno_frame
- [x] GlobalExcpetionHander.java 코드 변경 ⏫ ✅ 2023-10-27
- [x] application.properties 내용 변경 ✅ 2023-10-27
- [x] keycloak.auth-server-url=https://oid-dev.eland.co.kr/ ✅ 2023-10-27
- [x] keycloak.resource=interface-dev -> demo-dev ✅ 2023-10-27
- [x] git 생성 완료 GIT : http://svn.elandsystems.com:8090/scm/git/2023/INNOLINK-API ✅ 2023-10-27
- [x] project 생성 : 명칭 innolink-api ✅ 2023-10-27


- [ ] Inno-Frame 작업
	 - [x] ResponseEntity 내용 수정 ✅ 2023-10-30
		1. errordegtail => status->error
		2. data field 삭제
		3. GlobalExceptionHandler 수정 (errorDetail 설정 하는 부분)
	- [x] base Entity -> enable (true, false), true default ✅ 2023-10-30
		1. 삭제 시 enable->false
		2. 조회 시 조건, enable-= true 인것만
		3. 업데이트 시 enable=true 인것만 
		4. (수정 보류 - 도급시 필요)
	- [ ] 배포 : C:\Users\han.sungyoup01\.m2\settings.xml 확인 후 admin 추가.
		1. 이메일로 명령어 전달 받음.

- [ ]  Innolink-API 작업
	1. custom user - api
		1. custom_user, custom_attribute, custom_group 에 저장.
		2. 저장 시 결과 노출 (성공 리스트 및 실패 리스트)
		3. ![[group-data-form（案例）.txt]]![[user-data-form（案例）.txt]]
		4. ![[example_json.txt]]