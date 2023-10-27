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

3. Data: Gaiaya 와 소통되는 custom user/attribute json 외 group
	1. [https://wiki.eland.co.kr/pages/viewpage.action?pageId=311230579](https://wiki.eland.co.kr/pages/viewpage.action?pageId=311230579) 

4. Jenkins 배포 서버: 
	1. 배포 구성 만들어야 함
	2. 서비스 링크: [로그인 [Jenkins]](http://krvaissodev03:8090/login?from=%2F)
	3. 

