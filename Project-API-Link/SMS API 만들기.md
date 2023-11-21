- 신입사원 등록 시, 발송
- 신입사원 리스트를 받아서 발송.
- ID 와 암호 (초기 암호는 initialpassword 저장.) 발송 (template Code 별)

- mobile 번호가 없는경우 저장 금지.

보내는 내용 : mobile no. 를 사용하여, username, groupname, initalpassword 를 전달 한다.

       Map<String, Object> queries = new HashMap<>();
        _/**  
         *_ _김창호_ 　  _18616773282  
         *_ _尤__陈__春_     _13761361984  
         *_ _朴__艺兰_     _18501609106  
         */_
        queries.put("PhoneNumbers", "18616773282"); // 최초 인증된 번호
	        queries.put("SignName", "中国衣恋集团");  
			queries.put("TemplateCode", "SMS_462770417"); // d  
			queries.put("TemplateParam", "{\"code\":\""+_getNewCode_()+"\"}");
       
newCode (인증코드) 저장소

- 암호 바꿀 때, (6개월마다 및 forgot password(확인 중))
- principle: getUserName, (login ID)
- LoginId=username -> mobile 번호를 찾는다.

forgot password:
keycloak 화면에서 forgot password 클릭-> api 호출 -> api 에서 sms 전송 -> 인증번호를 forgot password 화면에 입력 -> api 호출, -> 인증번호가 맞으면, 저장했던 링크 화면에 전송.

=====================
- 2개 api. sms 화면(x)
	- userName, mobile 전달 받음.
	- 사용자엣 sms 전달 
		- 본인인증 코드 (만들어서 전달)
		- db 에 저장 (디비 확인)
			- id
			- 시간
			- 코드

	- success 여부를 반환
- userName, mobile, 코드 전달받고
	- db 저장 데이터와 확인 후
		- 시간 내 전달 여부 확인
		- 코드 일치 여부 확인
		- 
	- success 여부 전달


email, mobile, sms 화면을 만든다.

모바일:...
이메일...
인증문자...
확인 클릭 시 return uri 로 돌린다.

1. get/username -> username 과 redirect uri
-> 인증문자를 phone no 보내준다.
, redirect uri.. 
username을 mobile and email 로 화면을 띄운다.
인증번호를 누르면..
redirect->url 로 redirect 시킨다.

2. 생성 계정 문자 전송 url 을 받아서 전송


전송 시 메세지는.. 내 getNewCode () 인증번호 를 같이 발송 합니다.
getNewCode() 는 생성해야 함.
