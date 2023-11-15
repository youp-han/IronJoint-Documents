 Group
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


Group, User 모두  realm_id 추가 해서 검색해야 함.