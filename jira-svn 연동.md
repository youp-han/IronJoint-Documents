
jira 와 svn 연동 방법 7.3.7 : [JIRA and SVN Integration Tutorial](https://www.softwaretestinghelp.com/jira-svn-integration/)
연동은 이미 되어 있음.

fslk svn Repository 등록: jira -> admin -> system -> add-ons -> subversion repositories

update 는 every hour 로 설정 되어 있다.


단순, 일반 test 화면 : [[TES-1] test 이슈 입니다. - Eland JIRA](https://jira.eland.co.kr/projects/TES/issues/TES-1?filter=allissues)

실제 사용화면:  FASS: [[FASS-1066] 운영과제 - (O2O) 연계이력상세 에러상세 컬럼추가 - Eland JIRA](https://jira.eland.co.kr/projects/FASS/issues/FASS-1066?filter=resolvedrecently) 

방법, subversion 등록, 
commit 시 이슈 번호 추가 : TES-1

1. 기존 ETASK 에서는 View Development Tools 가 Developers 에만 적용이 되어 있어서 
	1. Project Settings -> Users & Roles -> developers 에 이름 추가
	2. Project Settings -> Permission: Any logged in user 를 추가하면 subversion 이 보인다.
	3.  ETASK-24769

![[Pasted image 20250108163110.png]]

hook : [Script - SVN Hook PreCommit - 1 - 풀필먼트솔루션 - Eland WIKI](https://wiki.eland.co.kr/display/FSLN/Script+-+SVN+Hook+PreCommit+-+1)