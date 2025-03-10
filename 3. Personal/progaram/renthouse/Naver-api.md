[네이버 회원 프로필 조회 API 명세 - LOGIN](https://developers.naver.com/docs/login/profile/profile.md)
#### 응답 예시

{
  "resultcode": "00",
  "message": "success",
  "response": {
    "email": "openapi@naver.com",
    "nickname": "OpenAPI",
    "profile_image": "https://ssl.pstatic.net/static/pwe/address/nodata_33x33.gif",
    "age": "40-49",
    "gender": "F",
    "id": "32742776",
    "name": "오픈 API",
    "birthday": "10-01",
    "birthyear": "1900",
    "mobile": "010-0000-0000"
  }
}

#### 요청 예시

GET v1/nid/me HTTP/1.1
Host: openapi.naver.com
User-Agent: curl/7.43.0
Accept: */*
Content-Type: application/xml
Authorization: Bearer {네이버 로그인 인증 후 받은 접근 토큰 값}

### 6. 에러 코드

공통 에러 코드는 [여기](https://developers.naver.com/docs/common/openapiguide/errorcode.md)를 참조하세요.

에러 코드 설명 표
|HTTP 코드|에러 코드|에러 메시지|조치 방안|
|---|---|---|---|
|401|024|Authentication failed / 인증에 실패했습니다.||
|401|028|Authentication header not exists / OAuth 인증 헤더(authorization header)가 없습니다.||
|403|403|Forbidden / 호출 권한이 없습니다.|API 요청 헤더에 클라이언트 ID와 Secret 값을 정확히 전송했는지 확인해보시길 바랍니다.|
|404|404|Not Found / 검색 결과가 없습니다.|-|
|500|500|Internal Server Error / 데이터베이스 오류입니다.|서버 내부 에러가 발생하였습니다. 포럼에 올려주시면 신속히 조치하겠습니다.|

### 5. 출력 결과

회원의 네이버아이디는 출력결과에 포함되지 않습니다. 대신 프로필조회 api 호출 결과에 포함되는 'id'라는 값을 이용해서 회원을 구분하시길 바랍니다. 'id'값은 각 애플리케이션마다 회원 별로 유니크한 값으로, 같은 네이버 회원이라도 네이버 로그인을 적용한 애플리케이션이 다르면 id값이 다른 점 유념하시길 바랍니다. 또한 가이드상에는 명시안되어 있지만 출력결과에 포함된 'enc_id'라는 값은 내부적으로 쓰는 값이므로 애플리케이션 개발에서 사용할 일이 없다고 보면되겠습니다.

출력 결과 설명 표
|필드|타입|필수 여부|설명|
|---|---|---|---|
|resultcode|String|Y|API 호출 결과 코드|
|message|String|Y|호출 결과 메시지|
|response/id|String|Y|동일인 식별 정보  <br>네이버 아이디마다 고유하게 발급되는 유니크한 일련번호 값  <br>(API 호출 결과로 네이버 아이디값은 제공하지 않으며, 대신 'id'라는 애플리케이션당 유니크한 일련번호값을 이용해서 자체적으로 회원정보를 구성하셔야 합니다.)|
|response/nickname|String|Y|사용자 별명  <br>(별명이 설정되어 있지 않으면 id*** 형태로 리턴됩니다.)|
|response/name|String|Y|사용자 이름|
|response/email|String|Y|사용자 메일 주소  <br>기본적으로 네이버 내정보에 등록되어 있는 '기본 이메일' 즉 네이버ID@naver.com 값이나, 사용자가 다른 외부메일로 변경했을 경우는 변경된 이메일 주소로 됩니다.|
|response/gender|String|Y|성별  <br>- F: 여성  <br>- M: 남성  <br>- U: 확인불가|
|response/age|String|Y|사용자 연령대|
|response/birthday|String|Y|사용자 생일(MM-DD 형식)|
|response/profile_image|String|Y|사용자 프로필 사진 URL|
|response/birthyear|String|Y|출생연도|
|response/mobile|String|Y|휴대전화번호|


### 2. API 기본 정보

API 기본 정보 설명 표
|메서드|인증|요청 URL|출력 포맷|설명|
|---|---|---|---|---|
|GET|OAuth 2.0|https://openapi.naver.com/v1/nid/me|JSON|네이버 회원 프로필 조회|

### 3. 요청 변수

요청 변수는 별도로 없으며, 요청 URL로 호출할 때 아래와 같이 요청 헤더에 접근 토큰 값을 전달하면 됩니다.

### 4. 요청 헤더

요청 헤더 설명 표
|요청 헤더명|설명|
|---|---|
|Authorization|접근 토큰(access token)을 전달하는 헤더  <br>다음과 같은 형식으로 헤더 값에 접근 토큰(access token)을 포함합니다. 토큰 타입은 "Bearer"로 값이 고정돼 있습니다. Authorization: {토큰 타입] {접근 토큰]|

#### 요청 헤더 예

Authorization: Bearer AAAAOLtP40eH6P5S4Z4FpFl77n3FD5I+W3ost3oDZq/nbcS+7MAYXwXbT3Y7Ib3dnvcqHkcK0e5/rw6ajF7S/QlJAgUukpp1OGkG0vzi16hcRNYX6RcQ6kPxB0oAvqfUPJiJw==

