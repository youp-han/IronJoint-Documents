1. 도급 등록 : [ELAND Identity Management](http://id.eland.com/) ( 처럼.. )
2. api 를 통한 HR JSON 리스트 등록
	1. application-dev.properties 의 DB 정보입니다.

#database
spring.datasource.username=keycloak
[spring.datasource.password=open@1209High](mailto:spring.datasource.password=open@1209High)
spring.datasource.url=jdbc:postgresql://10.123.253.111:5432/keycloak
#jpa
spring.jpa.defer-datasource-initialization=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

Gaiaya 와 소통되는 custom user/attribute json 외 group
[https://wiki.eland.co.kr/pages/viewpage.action?pageId=311230579](https://wiki.eland.co.kr/pages/viewpage.action?pageId=311230579) 