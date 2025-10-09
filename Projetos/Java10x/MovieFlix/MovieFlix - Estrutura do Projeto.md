___
- No site do [Spring Initializr](https://start.spring.io/) vamos fazer as seguintes configurações:
![[Pasted image 20251006232456.png]]
- Dependências:
	- Lombok
	- Spring Web
	- Spring Security
	- Spring Data JPA
	- Flyway Migration
	- PostgreSQL Driver
	- Validation
- Após a geração do projeto e abrirmos ele em nossa IDE, precisamos adicionar a dependência do ***JWT***, que podemos pegar no [MVN Repository](https://mvnrepository.com/artifact/com.auth0/java-jwt)
```xml
<dependency>
    <groupId>com.auth0</groupId>
    <artifactId>java-jwt</artifactId>
    <version>4.5.0</version>
</dependency>
```
- Agora em nosso arquivo `application.properties`, fazemos a alteração dele para `application.yaml`e fazemos as seguintes configurações:
```yaml
spring:
	application:
		name: movieflix
		
	datasource:
		url: jdbc:postgresql://localhost:5432/
		username: admin
		password: admin
		driver-class-name: org.postgresql.Driver
	
	jpa:
		database-plataform: org.hibernate.dialect.PostgreSQLDialect
		show-sql: true
		
	flyway:
		enabled: true
```