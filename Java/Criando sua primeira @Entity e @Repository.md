___
### Configurando o banco de dados
- Para podermos configurar a nossa conexão com o banco de dados precisamos adicionar algumas configurações no arquivo ***`application.properties`***.
- As propriedades são as mesmas independente do banco de dados utilizado, apenas são alterado seus valores
```properties
# Configurando conexão com banco de dados
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=password
spring.jpa.database-plataform=org.hibernate.dialect.H2Dialect

# Habilitando o console do H2 -> Configuração especifica
spring.h2.console.enabled=true
```
- Onde:
	- ***`spring.datasource.url`*** -> é a url para o nosso banco de dados;
	- ***`spring.datasource.driverClassName`*** -> aqui é o driver do banco de dados que vamos utilizar
	- ***`spring.datasource.username`*** -> credencial de acesso ao banco de dados configurado
	- ***`spring.datasource.password`*** -> credencial de acesso ao banco de dados configurado
	- ***`spring.jpa.database-plataform`*** -> É o dialeto que o `hibernate`, vai utilizar para as query's em sql;
### Acessando o Console do h2
- Ao subirmos a nossa aplicação para podermos acessar o painel do *h2*, usamos a url abaixo:
```url
http://localhost:8080/h2-console
```

### @Entity
- Uma entidade é basicamente uma referência para uma tabela do nosso banco de dados
- Criamos a nossa entidade como no exemplo abaixo:
```java
@Entity
@Table(name = "tb_users")
public class UserEntity {	}
```
- Onde:
	- ***`@Entity`*** -> Marca a nossa classe como uma entidade JPA
	- ***`@Table`*** -> Especifica a tabela no banco de dados que corresponde à entidade
- Para termos as nossas colunas, adicionamos atributos dentro dessa classe.
- Todas as tabelas precisam ter uma chave primária
```java
@Entity
@Table(name = "tb_users")
public class UserEntity {
	
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long userId;
	
	@Column(name = "username")
	private String name;
	
}
```
- Onde:
	- ***`@Id`*** -> Indica o identificador único da entidade
	- ***`@GeneratedValue`*** -> Configura a estratégia de geração automática de valores para a chave primária, permitindo que o banco de dados gere IDs únicos para novas entidades
	- ***`@Column`*** -> Define os detalhes da coluna correspondente ao atributo da entidade.
- Para que o **JPA** consiga interagir com a nossa entidade precisamos de todos os métodos ***Getters e Setters*** e também um *construtor vazio*;

### @Repository
- O `@Repository` é o responsável pela conexão entre a nossa `@Entity` e o banco de dados;
- Para criarmos um `@Repository`, podemos fazer como no exemplo abaixo:
```java
@Repository
public interface UserRepository extends JpaRepository<Entidade, TipoDoIdDaEntidade> {}
```
- O `@Repository`não é obrigatório;