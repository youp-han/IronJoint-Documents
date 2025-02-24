old server -> 10.123.185.245
to server ->  10.123.253.123

배포 서버
개발 :
   was.path=D:/Jenkins/KRCP_Admin
   was.path=D:/Jenkins/KRCP_Web
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
	was.pass=krcp+0513
	was.type=prd
	was.path=D:/Jenkins/KRCP_Admin
	was.ip=10.123.250.146
	was.user=deploy
	was.pass=krcp+0513
	was.type=prd
	was.path=D:/Jenkins/KRCP_Admin


|담당자|
개발 |서은정, 김지혜, 김대근, 박유진, 이우영||
운영 |김지혜, 김대근, 박유진, 이우영|   |