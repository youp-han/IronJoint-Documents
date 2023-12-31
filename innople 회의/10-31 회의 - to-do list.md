1. Group
	1. parent_group_code
	2. level x -> 버릴 예정
2. User
	1. 신규가입 email 생성 어떻게 하는지 확인

**1. Group insert / update**

 1. Group request 수신 시 Entity build
- [x] 2. Group name check ✅ 2023-11-10
	- [x] 그룹명 양옆 공백제거 ✅ 2023-11-02
	- new 그룹 데이터와 기존 그룹 간 같은 그룹명이 존재하면 안됨. 
	- [x] 그룹명 중복시 01, 02... 넘버링 하여 그룹명 뒤에 append ✅ 2023-11-10

  - [x] 3. 신 구 그룹데이터 비교하여 update 및 insert ✅ 2023-11-10
  - [x] - 테이블 내 group_code 컬럼을 key값으로 비교 ✅ 2023-11-10
  - [x] - 같은 Group이라면 update, 생성 날짜 기재 ✅ 2023-11-10
  - [x] - 없는 Group이라면 insert, 수정 날짜 기재 ✅ 2023-11-10
  - [x] - 없어진 그룹은 delete 컬럼 true로 update, 수정 날짜 기재 ✅ 2023-11-10
  - [x] parent-group-code 수정 가능 ✅ 2023-11-10

**2. User insert / update**

modifiedUser 추가
realm  데이터 넣기
- [x] roles = "user" 디폴트로 추가해 주기 ✅ 2023-11-10

- [x] Controller -> Service customuserDto 로 주고 받기.

- [x] @Service 위에 @Transactional 넣기
GetAll 시

- [ ] request data 에서 중복 검사
- [ ] username 앞 뒤 공백제거
- [ ] username 검사 후 중복 시 넘버링
- [ ] DB에는 컬럼이 존재하지만 request data에 없는데이터는 직접 생성하여 넣어줘야함
- [ ] 계정 생성/가입시 - email, 사번, 계정 유형(도급, 정규)
- [x] create_user 컬럼은 어디에서 만들어졌는지 판단하기 위한 정보성 컬럼(KEYCLOAK, NEWIAM, GAIYA) ✅ 2023-11-10 sysetm account



Custom user 테스트 케이스
[4.6.0.2 통합계정 Test 시나리오 - 3G연구소 - Eland WIKI](https://wiki.eland.co.kr/pages/viewpage.action?pageId=311985745) 

- 테스트 데이터 저장 확인
- 등록 결과 회신 데이터 확인: 성공/실패 데이터 리스트 회신
- 중복 이름 userName: 넘버링 테스트:
    1. 한승엽 - 기존 데이터
    2. 한승 으로 입사처리: 한승 으로 생성
    3. 한승 동명이인 입사처리: 한승01로 생성


필수값. 
GroupCode 없으면 "부서코드 없음" 오류.
employeeId 는 무조껀 숫자. -> 사원코드 오류
mobile, exemail (이메일 형태) 은 필수값. -> 연락처 오류
birthday, hireddate 필수
persg -> 필수 숫자.
createdDate 필수

firstName, lastName 둘다  없으면 : 이름 오류

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
- [ ] 1. 보내준 데이터에는 employeeId 이 존재 하고, 검색한 테이블에 해당 사번의 custom user 존재, 보내준 데이터에는 username 없음 → 사번 중복 오류 (동일 사번으로 계정 생성할 수 없음)
 - [ ] 2. employeeId 과 username 이 같으면 update 처리
 - [ ] 3. employeeId 는 같은데 username 이 다르면 계정 변경 요청을 처리 불가
 - [ ] 4. emplpyeeId 로 등록된 데이터가 없고 username 이 비어있으면 신입 사원처리 (계정 추가)

- [x] 계정, username, email 이 없는경우 신입사원. ✅ 2023-11-11
	- [ ] 신입사원 확인. (여부) 
	- [x] 사번 확인. ✅ 2023-11-11
	- [x] 사번 중복인 경우, (오류) 이미 등록된 user ${username} 입니다. ✅ 2023-11-11
	- [x] 사번이 없는경우 : 신입사원 진행 ✅ 2023-11-11
- 
	- [ ] 신입사원  만드는 방법
		- [x] lastname+ "_______"+ firstname. ✅ 2023-11-11
		- [x] 중복 확인 후 중복인  경우 넘버링 추가. (코드 수정. regularexpression 으로 넘버링 확인) ✅ 2023-11-11
		- [ ] 테스트) input: 한승, -> db data: 한승엽

delete from CUSTOM_USER_ATTRIBUTE;
delete from  CUSTOM_USER;

delete from CUSTOM_GROUP ;



