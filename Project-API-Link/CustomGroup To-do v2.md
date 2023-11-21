 Group
	2. level x -> 버릴 예정
* json String 을 바로 entity 에 넣어서 작업 진행 중 (no dto)*



**1. Group insert / update**

- [x] 1. Group request 저장 ✅ 2023-11-15
- http://localhost:8080/api/group
- - http://localhost:8080/api/group/list
1. 테이블 내 group_code 컬럼을 key값으로 비교 
2. groupCode 부재 시 오류
3. groupName 부재 시 오류
4. parentGroupCode 부재 시 오류
5. groupCode 존재 확인
	1. 쿼리결과, GroupCode 존재 시 업데이트
		1. realmId, groupCode 확인
			1. 업데이트 할 groupName 확인
			2. parentGroupCode 업데이트
			3. name 업데이트
	2. 쿼리결과, GroupCode 미 존재 시 추가
		1. reamId 추가
		2. eabled = true
		3. name 업데이트

**2. Group Delete 

- [x] 2. Group request 삭제 (전체 업데이트 시) ✅ 2023-11-15
- http://localhost:8080/api/group/list
6. 전체 업데이트 시 저장은 1번과 동일
7. 저장 진행 완료 후, 삭제 대상 존재 여부 검색
	1. 삭제 대상이 있는 경우
		1. 저장된 리스트 에서 isEnabled = true 인 데이터만 리스트 만들고
		2. 저장 대상 리스트 와 비교하여 삭제 리스트 생성
		3. 삭제 진행

--------------------------------------------------------------------		
- [x] 3, Group name check ✅ 2023-11-15
	 1. 그룹명 양옆 공백제거 
	 2. new 그룹 데이터와 기존 그룹 간 같은 그룹명이 존재하면 안됨. 
		 1. 그룹명 중복시 01, 02... 넘버링 하여 그룹명 뒤에 append 
	 3. 신 구 그룹데이터 비교하여 update 및 insert 
	 4.  parent_group_code 업데이트 가능




Group, User 모두  realm_id 추가 해서 검색해야 함.