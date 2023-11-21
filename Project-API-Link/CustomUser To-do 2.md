
**1. CustomUser 등록

- [x] CustomUser 등록 ✅ 2023-11-15
- http://localhost:8080/api/customuser
1. employeeId 부재시 오류, 숫자가 아니면 오류
2. GroupCode 부재 시 오류
3. GroupName 부재시 오류
4. 둘다 없을 때, mobile, exemail (이메일 형태) 은 필수값. -> 연락처 오류
5. birthday, hireddate 필수
6. persg -> 필수 숫자. -> attribute 로 이동 (x)
7. createdDate 필수
8. firstName, lastName 둘다  없으면 : 이름 오류
9.  오류계정
		1. employeeId 가 중복 아님
		2. exeMail 정보로 검색된 email 을 가진 결과가 있는경우
			- new data 의 exemail == oldata 의  email 인경우 (오류처리)
		3. "중복오류"
10. employeeId 를 이용하여 중복 데이터 확인
	1.  **없으면 저장
		1. 신규 계정 확인
			1. userName, email 확인. 없으면 신규 계정
			2. 신규 계정 시 userName 생성 및 추가
				1. 정직원 (88888888)
					1.  lastName_firstName
				2. 지사스텝 (11111111)
					1. lastName.firstName
				3. 신소매 (5555555555)
					1. lastName.firstName
				4. SPA 직원(9999999999)
					1. shop-employeeId
		2. userName unique 확인
		3. createUser 추가 (principal.getName())
		4. realm  데이터 넣기
		5. reles = "user" 디폴트로 추가

	2. **있으면 업데이트
		1. userName 이 없으면 오류
			1. 사번 중복 오류
		2. userName 이 중복된 사번의 userName 과 같으면 오류
			1. 계정명 변경 불가 오류
		3. modifiedUser 추가
			
**2. CustomUser 삭제	

- [x] CustomUser 삭제 ✅ 2023-11-15
- - http://localhost:8080/api/customuser/list
전체 업데이트 시 저장은 1번과 동일
1. 저장 진행 완료 후, 삭제 대상 존재 여부 검색
	1. 삭제 대상이 있는 경우
		1. 저장된 리스트 에서 isEnabled = true 인 데이터만 리스트 만들고
		2. 저장 대상 리스트 와 비교하여 삭제 리스트 생성
		3. 삭제 진행


----------------------------------------------------------------
1. 신규가입 email 생성 어떻게 하는지 확인

modifiedUser 추가
realm  데이터 넣기
- roles = "user" 디폴트로 추가해 주기
- Controller -> Service customuserDto 로 주고 받기.
- @Service 위에 @Transactional 넣기
- GetAll 시 @Transactional(readOnly = true)

- request data 에서 중복 검사
- username 앞 뒤 공백제거
- username 검사 후 중복 시 넘버링
- DB에는 컬럼이 존재하지만 request data에 없는데이터는 직접 생성하여 넣어줘야함
- 계정 생성/가입시 - email, 사번, 계정 유형(도급, 정규)
- create_user 컬럼은 어디에서 만들어졌는지 판단하기 위한 정보성 컬럼(KEYCLOAK, NEWIAM, GAIYA) 



Custom user 테스트 케이스
[4.6.0.2 통합계정 Test 시나리오 - 3G연구소 - Eland WIKI](https://wiki.eland.co.kr/pages/viewpage.action?pageId=311985745) 

저장시

modifiedUser 추가
realm  데이터 넣기
reles = "user" 디폴트로 추가해 주기

Controller -> Service customuserDto 로 주고 받기.

@Service 위에 @Transactional 넣기
GetAll 시




CustomUser
list -> 전체 데이터 일때만 삭제
list -> 업데이트/추가 데이터일때는 삭제 진행 안함.

도급직 ->시작날짜 엔드날짜.

중국측 신입사원.
- AD OU  사번 관련  - OU 구조는 유지하고자 함.  - 5가지 직원형태 -> 3가지 OU  - 정직원    - 8시작 8자리     - -> AD 직원     - piao_yilan  
  - 지사스텝 (런리워)    - 1시작 8자리     - -> AD런리워    - piao.yilan  
  - 신소매 (리셀러 개념)    - 5로 시작 10자리    - -> AD런리워    - piao.yilan  
  - SPA직원    - 9시작 10자리    - ->AD외주직원 

    - shop-사번


- 중복 데이터 점검:
-  1. 보내준 데이터에는 employeeId 이 존재 하고, 검색한 테이블에 해당 사번의 custom user 존재, 보내준 데이터에는 username 없음 → 사번 중복 오류 (동일 사번으로 계정 생성할 수 없음) ✅ 2023-11-15
 - 2. employeeId 과 username 이 같으면 update 처리 ✅ 2023-11-15
 -  3. employeeId 는 같은데 username 이 다르면 계정 변경 요청을 처리 불가 ✅ 2023-11-15
 - 4. emplpyeeId 로 등록된 데이터가 없고 username 이 비어있으면 신입 사원처리 (계정 추가) ✅ 2023-11-15

- [x] 계정, username, email 이 없는경우 신입사원. ✅ 2023-11-11
	- 신입사원 확인. (여부) ✅ 2023-11-15
	- 사번 확인. ✅ 2023-11-11
	- 사번 중복인 경우, (오류) 이미 등록된 user ${username} 입니다. ✅ 2023-11-11
	-  사번이 없는경우 : 신입사원 진행 ✅ 2023-11-11
- 
	- [ ] 신입사원  만드는 방법
		- lastname+ "_______"+ firstname. ✅ 2023-11-11
		-  중복 확인 후 중복인  경우 넘버링 추가. (코드 수정. regularexpression 으로 넘버링 확인)
		- 테스트) input: 한승, -> db data: 한승엽


Group, User 모두  realm_id 추가 해서 검색해야 함.

update 문제는 dto 에 id 필드를 넣고 확인.

신입사원일 때 initial password 를 만들어 추가한다.
함수는 서영우님에게 받기.

- 업데이트 추가된 사항

employeeid (사번)이 달라도, exemail 로 검색하여 
exemail 에 userName@eland.co.kr 이 있으면, 
email 계정이 기존에 등록된게 있으면, 계정을 이어준다. 
- userName 이 동일해야 한다. not userName01

발령자:
new 사번은 다르고, new exeMail 의 계정으로 userName 을 만들어야 하는데, 
기존에 동일한 userName 이 존재하면 순번을 올리지 않고, 오류로 처리한다.
(중복오류:) 이미 등록된 userName 이 존재합니다.



한국직원 A (old data)
id : seo_youngwoo
pw : 1234
email : [seo_youngwoo@eland.co.kr](mailto:seo_youngwoo@eland.co.kr "mailto:seo_youngwoo@eland.co.kr")
exmail : [devsyw@gmail.com](mailto:devsyw@gmail.com)

한국직원 A가 중국으로 갔을때 (new data)
id : seo_youngwoo (sync) <-- 동일하게 유지 (x) 안함 오류 케이스
pw : 1234 (sync)
email : [seo_youngwoo@elandfashion.cn](mailto:seo_youngwoo@elandfashion.cn "mailto:seo_youngwoo@elandfashion.cn")
exmail: [seo_youngwoo@eland.co.kr](mailto:seo_youngwoo@eland.co.kr "mailto:seo_youngwoo@eland.co.kr") (sync key)

createdUser
realmId
initial_password (신입사원만)