___
- No site do [Spring Initializr](https://start.spring.io/), vamos configurar o nosso projeto.
- As dependências que vamos utilizar são:
	- Spring Web
	- Spring Data JPA
	- MySQL Driver
	- Validation
- Vamos gerar o projeto e abrir em nossa IDE.
- Na raiz do nosso projeto, vamos criar o arquivo `docker-compose.yml`
```yml
services:
	mysql:
		image: mysql:latest
		environment:
			- MYSQL_USER=jbank
			- MYSQL_PASSWORD=secret
			- MYSQL_DATABASE=jbankdb
			- MYSQL_ROOT_PASSWORD=123
		ports:
			- 3306:3306    
```
- Agora podemos subir o container com o comando:
```zsh
docker compose up -d
```
- Agora podemos tentar abrir esse banco de dados através da ferramenta do *Beekeeper* para podermos ver se o banco de dados subiu corretamente;
- Agora em no arquivo ***`application.properties`***, vamos adicionar as configurações:
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/jbankdb
spring.datasource.username=jbank
spring.datasource.password=secret
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```
- Desta maneira nossa aplicação já está conectada com o nosso banco de dados;
- Desta maneira podemos tentar rodar a nossa aplicação para verificar se está tudo certo.