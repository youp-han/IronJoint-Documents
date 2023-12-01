[https://oid-dev.eland.co.kr/api/interface/messaging/{templateId}](https://oid-dev.eland.co.kr/api/interface/messaging/%7btemplateId%7d)

POST

request body:

{
  "receivers": [
    {
      "username": "han.sungyoup01"
    },  
    {
      "username": "seo_youngwoo02"
    },  
    {
      "username": "lee_kyungmu"
    },
]
}

response
{
  "status": "ok",
  "data": [
    {
      "username": "han.sungyoup01",
      "smsId": "f3eb2cf2-28f7-4ae7-b833-03d25146fd42",
      "exemail": "[han.sungyoup01@naver.com](mailto:han.sungyoup01@naver.com)",
      "mobile": "010-000-0000",
      "status": "processing",
      "message": ""
    },  
    {
      "username": "seo_youngwoo02",
      "smsId": "f3eb2cf2-28f7-4ae7-b833-03d25146fd42",
      "exemail": "",
      "mobile": "",
      "status": "error",
      "message": "ContactNotExist"
    },  
    {
      "username": "lee_kyungmu",
      "smsId": "f3eb2cf2-28f7-4ae7-b833-03d25146fd42",
      "exemail": "[lee_kyungmu@gmail.com](mailto:lee_kyungmu@gmail.com)",
      "mobile": "010-000-0000",
      "status": "processing",
      "message": ""
    },

  ],

  "count": 3

}

발송결과 확인

[https://oid-dev.eland.co.kr/api/interface/sms/{templateId}?page=1&size=20&sort=username,asc](https://oid-dev.eland.co.kr/api/interface/sms/%7btemplateId%7d?page=1&size=20&sort=username,asc)

GET

{

  "status": "ok",

  "data": [  
    {

      "username": "han.sungyoup01",

      "smsId": "f3eb2cf2-28f7-4ae7-b833-03d25146fd42",

      "exemail": "[han.sungyoup01@naver.com](mailto:han.sungyoup01@naver.com)",

      "mobile": "010-000-0000",

      "status": "ok",

      "message": ""

    },  
    {

      "username": "seo_youngwoo02",

      "smsId": "f3eb2cf2-28f7-4ae7-b833-03d25146fd42",  
      "exemail": "",

      "mobile": "",

      "status": "error",

      "message": "ContactNotExist"

    },  
    {

      "username": "lee_kyungmu",

      "smsId": "f3eb2cf2-28f7-4ae7-b833-03d25146fd42",

      "exemail": "[lee_kyungmu@gmail.com](mailto:lee_kyungmu@gmail.com)",

      "mobile": "010-000-0000",  
      "status": "error",

      "message": "Fail to send SMS: There is no customer with phone number."

    },

  ],

```
  "pageable": {
```

```
    "sort": {
```

```
      "sorted": true,
```

      `"unsorted": false,`

      `"empty": falsez`

    `},`

```
    "offset": 20,
```

    `"pageNumber": 1,`

    `"pageSize": 20,`

    `"paged": true,`

    `"unpaged": false`

```
  },
```

```
  "count": 3
```

}

template id:

임시비번=

본인인증=

[@이경무(이노플 InfraTech(AA))](mailto:LEE_KYUNGMU@elandinnople.com), [@서영우(이노플 InfraTech(AA))](mailto:SEO_YOUNGWOO02@elandinnople.com)

모바일 번호 없는 사람의 메일 전송을 위해 제목과 본문 내용을 알려주세요

[@한승엽(파트너사 (주)유비템즈)](mailto:Han.SungYoup01@eland-partner.co.kr) 차장님

위 내용 받으셔서 messages.properties 에 등록하고 사용하세요

mail.template.{template-id}.title=han.sungyoup01님의 본인인증 메일입니다.

mail.template.{template-id}.body=han.sungyoup01님, 안녕하세요.<br/>본인 인증을 위해서 입력하실 인증번호는 아래와 같습니다....