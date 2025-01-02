EKKS
- server: 10.252.34.183 (linux?)
- jdk1.8.0_92
- maven : 3.6.3
- git : http://svn.elandsystems.com:8090/scm/git/2020/EBKS_Project
- 배포 : aws code deploy

EIMS
- Server : 10.123.50.51 (linux?)
- DEV_RCRM_EIMS_LOYALTY
	- jdk1.7.0_75
	- maven : 3.3.9
	- svn : http://krsapvcsdv01:8090/scm/svn/2017/RCRM_Project/branch/GNEIMS/Loyalty
	- 로컬 파일 카피
	- user: ???
	
- DEV_RCRM_EIMS_OneClickApi
	- jdk 1.8.0_92
	- svn: http://krsapvcsdv01:8090/scm/svn/2017/RCRM_Project/branch/GNEIMS/LoyTxnOneClickApi
	- Maven 3.3.9
	- ssh to IP 10.123.185.98
	- user: eland_user
	
- DEV_RCRM_EIMS_PartnerApi
	- Server : KRVROCBDEV01 (121.190.88.200) : windows
	- jdk1.7.0_75
	- Maven 3.3.9
	- svn: http://krsapvcsdv01:8090/scm/svn/2017/RCRM_Project/branch/GNEIMS/LoyTxnPartnerApi 	- 
	- 배포 -> 로컬 파일 카피
	
- DEV_RCRM_EIMS_TXNSERVER_JAR
	- jdk 1.8.0_92
	- Maven 3.3.9
	- svn: http://krsapvcsdv01:8090/scm/svn/2017/RCRM_Project/branch/GNEIMS/LoyTxnServer@$REV
	- 배포: secure copy (scp) to 10.123.50.53
	- user: elanduser
	-
- DEV_RCRM_EIMS_PosApi
	- jdk 1.8.0_92
	- Maven 3.3.9
	- svn: http://krsapvcsdv01:8090/scm/svn/2017/RCRM_Project/branch/GNEIMS/LoyPosApi
	- 배포 : ssh to 10.123.50.53
	- user = elanduser

RDRC
- DEV_RCRM_EIMS_IGIGNAL_ADMIN
	- jdk 1.8.0_92
	- Maven 3.3.9
	- svn http://krsapvcsdv01:8090/scm/svn/2017/RCRM_Project/branch/RDRC/iGignal_Admin
	- 배포: ssh to 10.123.50.103(dev)
	- prd: IP=10.123.40.163,10.123.40.164
	- USER=mktadmin

ERCS
- DEV_RCRM_ERCS
	- jdk1.7.0_75
	- maven : 3.3.9
	- svn: http://krsapvcsdv01:8090/scm/svn/2017/RCRM_Project/trunk/ERCS 
	- 배포: ssh
		- IP=10.123.50.100
		- USER=mktadmin
- PRD_RCRM_ERCS
	- 배포 : ssh
		- IP: 10.123.183.21, 10.123.183.22
		- USER=mktadmin