___
- Algumas variáveis são sensíveis, e precisamos deixar elas de maneiras ocultas;
- As maneira mais comum é usando um arquivo `.env`, e para fazer isso criamos esse arquivo na raiz do nosso projeto.
- E nesse arquivo colocamos as informações sensíveis, como no exemplo abaixo:
```.env
DATABASE_URL=jdbc:h2:mem:testdb;DB_CLOSE_DELAY=-1;DB_CLOSE_ON_EXIT=FALSE
DATABASE_USERNAME=cadastro_bd
DATABASE_PASSWORD=cadastro_bd
```
- E agora para usarmos as variáveis genéricas, voltamos ao arquivo `application.properties` e seguimos como no exemplo abaixo:
```properties
spring.datasource.url=${DATABASE_URL}
spring.datasource.username=${DATABASE_USERNAME}
spring.datasource.password=${DATABASE_PASSWORD}
```
- Agora precisamos configurar essas variáveis nas configurações do projeto