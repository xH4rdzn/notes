___
- Para poder configurar o H2, em nosso projeto precisamos adicionar a dependência dele em nosso projeto primeiramente.
- Para fazer isso adicionamos o código abaixo no arquivo `pom.xml`
```xml
<dependency>
      <groupId>com.h2database</groupId>
      <artifactId>h2</artifactId>
      <scope>runtime</scope>
</dependency>
```
- Como o H2 é um banco de dados em memória, podemos acessar ele pelo nosso navegador, na URL abaixo:
```url
localhost:8080/h2-console
```
- Agora vamos na pasta *resources* e dentro dessa pasta vamos ter o arquivo `application.properties`;
- Esse arquivo é onde vamos colocar todas as nossas configurações relacionadas a nossa aplicação, inclusive o banco de dados;
- Nesse arquivo adicionamos as seguintes linhas:
```properties
spring.datasource.url= jdbc:h2:mem:testdb
spring.datasource.driver = org.h2.Driver
spring.datasource.username = cadastro_bd
spring.datasource.password =
```
- Independente do banco de dados, o que muda são apenas os valores;
- Mas como o **H2** é um banco de memória, quando ele ficar sem uso ele apaga os dados, para que isso não ocorra, adicionamos a seguinte configuração:
```properties
spring.datasource.url=jdbc:h2:mem:testdb; DB_CLOSE_DELAY=-1;DB_CLOSE_ON_EXIT=FALSE
spring.datasource.driver=org.h2.Driver
spring.datasource.username=cadastro_bd
spring.datasource.password=
```
- Agora também precisamos fazer a configuração do *JPA*, então adicionamos o seguintes códigos:
```properties
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.h2.console.enabled=true
```
- Após isso tentamos subir a nossa aplicação;