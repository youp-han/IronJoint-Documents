1. 로그인 문제
	1. 생성 되다 만 계정 은
		1. innowas01, 02 로그 확인 시 fail, modify error 가 뜸
		2. adexplorer 에서 enald-china.com->china->members 검색 (username)
		3. 상태가 주로 512 이지만, 아닌 문제인 경우는 512가 아님
		4. sso (keycloak) 에 연결하여 username 검색 시 생성됨. (끝)
	2. 생성 다 되었는데, 0xFFFFFFF 오류인 경우엔
		1. 10.201.10.218 에 연결하여 active directory suers and computers 
		2. 사용자 검색 -> Account expires 를 end of 로 고치고 apply, 다시 never 로 고치고 apply 한다.
		3. 0xFFFFFFF -> 0x0 으로 바뀌면 성공
