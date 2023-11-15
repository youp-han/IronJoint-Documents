 Group
	1. parent_group_code
	2. level x -> 버릴 예정
	3. 


**1. Group insert / update**

- [ ] 1. Group request 저장
- http://localhost:8080/api/group
1. GroupCode 부재 시 오류
2. GroupName 부재 시 오류
3. ParentGroupCode 부재 시 오류
4. GroupCode 존재 확인
	1. 쿼리결과, GroupCode 존재 시 업데이트
		1. realmId, groupCode 확인
			1. 업데이트 할 groupName 확인
			2. parentGroupCode 업데이트
			3. name 업데이트
	2. 쿼리결과, GroupCode 미 존재 시 추가
		1. reamId 추가
		2. eabled = true
		3. name 업데이트

- [ ] 2. Group request 삭제 (전체 업데이트 시)
- http://localhost:8080/api/group/list
1. 전체 업데이트 시 저장은 1번과 동일
2. 저장 진행 완료 후, 삭제 대상 존재 여부 검색
	1. 삭제 대상이 있는 경우
		1. 저장된 리스트 에서 isEnabled = true 인 데이터만 리스트 만들고
		2. 저장 대상 리스트

		
- [ ] 3, Group name check
	 1. 그룹명 양옆 공백제거 
	 2. new 그룹 데이터와 기존 그룹 간 같은 그룹명이 존재하면 안됨. 
	 3. 그룹명 중복시 01, 02... 넘버링 하여 그룹명 뒤에 append 
	 4. 신 구 그룹데이터 비교하여 update 및 insert 
	 5. 테이블 내 group_code 컬럼을 key값으로 비교 
	 6. 같은 Group이라면 update, 생성 날짜 기재 
	 7. 없는 Group이라면 insert, 수정 날짜 기재 
	 8. 없어진 그룹은 delete 컬럼 true로 update, 수정 날짜 기재 
	 9. parent-group-code 수정 가능 


Group, User 모두  realm_id 추가 해서 검색해야 함.