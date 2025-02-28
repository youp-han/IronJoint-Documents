old server -> 10.123.185.245 
http://10.123.185.245:8080/

to server ->  10.123.253.123
http://10.123.253.123:8080/ 

- build java version 
	- jdk-12.0.2 (설치함)
- maven
	- Maven 3.6.3
- 

- git: http://svn.elandsystems.com:8090/scm/git/2022/KRCP_Project 
- branch
	- develop
	- master

빌드: mvn clean package
Coms/pom.xml 


ssh 포트 오픈 요청 필요

source : 10.123.253.123
destination: 
- 개발 10.123.253.83, / KRCP_DEV
- 운영1: 10.123.250.145 / KRCP_PRD01
- 운영 2: 10.123.250.146 / KRCP_PRD02
포트: 22



배포 서버
개발 :KRVAKRCPWEBQA01 : 10.123.253.83
ant 배포 -> 로컬 -> ssh 로 변경
Admin/build.xml -> target dev
- was.path=D:/Jenkins/KRCP_Admin
Web/build.xml -> target dev
- was.path=D:/Jenkins/KRCP_Web



운영:
- web
	- was.ip=10.123.250.145
	- was.user=deploy
	- was.pass=krcp+0513
	- was.type=prd
	- was.path=D:/Jenkins/KRCP_Web
	
	- was.ip=10.123.250.146
	- was.user=deploy
	- was.pass=krcp+0513
	- was.type=prd
	- was.path=D:/Jenkins/KRCP_Web
	
- admin
	- was.ip=10.123.250.145
	- was.user=deploy
	- was.pass=krcp+0513
	- was.type=prd
	- was.path=D:/Jenkins/KRCP_Admin
	-
	- was.ip=10.123.250.146
	- was.user=deploy
	- was.pass=krcp+0513
	- was.type=prd
	- was.path=D:/Jenkins/KRCP_Admin
- 

|담당자|
개발 |서은정, 김지혜, 김대근, 박유진, 이우영||
운영 |김지혜, 김대근, 박유진, 이우영|   |