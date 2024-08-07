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

2. api 문제
	1. log 에서 error-fail - modify account 오류가 남
		--> 신규 생성id 문제.
		--> 로그에서 fail 이 됨
		--> adexplorer 에서 확인 하여 545 인 경우 문제 (주로 512임)
			samaccount 에서 username 을 넣고 검색 
			(메일 생성 확인 : elandchina.cn : proxy 메일 확인) - ???
			
	1. keyCloak url 과 암호 (eland-china)
		sso.eland-china.com (admin/open@0123High)
		-- created 되다 말아서 계속 update 문제되는 account 로 확인 되면, 
		keycloak 에서 user_name 을 검색만 하면 ad 에서 자동 정보를 가지고 와서 update 된다.
		db 에서 해당 계정의 modified (modified_date 아님) 를 로컬 시간으로 변경하면, 다음 키클럭 실행 시 반영됨.
		
	1. keyclock 데이터 확인
		 - 사용자 확인: Keycloak -> eland-china ->users
		 - 동기화 : User Federation -> Custom User (custom_user 테이블 과 동기화)
		 - 상단 우축 Action -> Sync Changed users
		 - 		 - 동기화 : User Federation ->AD (AD테이블 과 동기화)
	