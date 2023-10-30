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

3. pom.xml 추가 내용

- 추가
<!-- tools -->  
<dependency>  
    <groupId>org.projectlombok</groupId>  
    <artifactId>lombok</artifactId>  
    <optional>true</optional>  
</dependency>

- 교체
<parent>  
    <groupId>org.springframework.boot</groupId>  
    <artifactId>spring-boot-starter-parent</artifactId>  
    <version>2.5.6</version>  
</parent>

<java.version>${java.version}</java.version> -> <java.version>17</java.version>


5. Data: Gaiaya 와 소통되는 custom user/attribute json 외 group
	1. [https://wiki.eland.co.kr/pages/viewpage.action?pageId=311230579](https://wiki.eland.co.kr/pages/viewpage.action?pageId=311230579) 

6. Jenkins 배포 서버: 
	1. 배포 구성 만들어야 함
	2. 서비스 링크: [로그인 [Jenkins]](http://krvaissodev03:8090/login?from=%2F)
	3. 

[SpringBoot JPA 예제(@OneToMany, 단방향) :: JDM's Blog](https://jdm.kr/blog/141)