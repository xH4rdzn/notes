___
- Para esse projeto vamos utilizar as seguintes dependências:
	- ***Spring Web***
	- ***Spring Data JPA***
	- ***PostgreSQL Driver***
- Ao abrir o projeto em nossa IDE, vamos configurar o nosso banco de dados.
- Na raiz do nosso projeto vamos criar o arquivo `docker-compose.yml`e dentro dele vamos fazer as seguintes configurações:
```yml
services:
	postgres:
		image: 'postgres:latest'
		environment:
			- 'POSTGRES_DB=ecommercedb'
			- 'POSTGRES_PASSWORD=secret'
			- 'POSTGRES_USER=user'
		ports:
			- '5432:5432'	  
```
- Após isso no nosso terminal podemos usar o comando abaixo para poder subir o nosso banco de dados:
```zsh
docker compose up -d
```
- Agora em nosso arquivo `application.properties`, vamos fazer a seguinte configuração:
```properties
spring.application.name=ecommerce  
  
spring.datasource.url=jdbc:postgresql://localhost:5432/ecommercedb
spring.datasource.username=myuser
spring.datasource.password=secret
spring.datasource.driver-class-name=org.postgresql.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database-plataform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.show-sql=true
```
