- 신입사원 등록 시, 발송
- ID 와 암호 (초기 암호는 사번) 발송 (template Code 별)
- mobile 번호가 없는경우 저장 금지.
- 
- 암호 바꿀 때, (6개월마다 및 forgot password(확인 중))
- principle: getUserName, (login ID)
- LoginId=username -> mobile 번호를 찾는다.

forgot password:
keycloak 화면에서 forgot password 클릭-> api 호출 -> api 에서 sms 전송 -> 인증번호를 forgot password 화면에 입력 -> api 호출, -> 인증번호가 맞으면, 저장했던 링크 화면에 전송.


username, redirect uri.. 
username을 mobile and email 로 화면을 띄운다.ㅏ

전송 시 메세지는.. 내 getNewCode () 인증번호 를 같이 발송 합니다.
getNewCode() 는 생성해야 함.
