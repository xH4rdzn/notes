___
- ***Hibernate*** -> Ele vai pegar o mapeamento da nossa classe e vai transformar em uma tabela do banco de dados.
- As `migrations`, são o versionamento das nossas tabelas do banco de dados.
- Vamos utilizar uma dependência chamada *Flyway*, que podemos baixar no **Spring Initilizer**
```xml
<dependency>
      <groupId>org.flywaydb</groupId>
      <artifactId>flyway-core</artifactId>
</dependency>
```
- Para podermos utilizar essa dependência, agora, dentro da pasta `resources`, vamos criar uma pasta chamada `database` e dentro dela podemos criar uma outra pasta chamada `migrations`;
- Para criar os arquivos de `migrations`, o nomeamos como no exemplo a seguir:
```text
VX__nome_migration.sql
```
- Onde o `X`, é o número da versão;
- E dentro desse arquivo colocamos o código em sql da mudança que queremos fazer no nosso  banco de dados;
- Agora em  `application.properties`, vamos adicionar:
```properties
spring.flyway.enable=true
spring.flyway.locations=classpath:database/migrations
spring.flyway.baseline-on-migrate=true
```