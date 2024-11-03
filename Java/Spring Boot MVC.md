___
### Você sabe o que é MVC ?
- Acrônimo de `Model-View-Controller`
- Padrão de Arquitetura de Software
- Foco na separação do código, de acordo com sua responsabilidade, em três camadas.
- `M (Model)` -> Responsável pelo acesso e tratamento de dados;
- `V (View)` -> Responsável pela Interface com o usuários;
- `C (Controller)` -> Camada intermediaria entre a `Model` e a `View`, e também é responsável pelas regras de negócio;

### Framework Spring Boot
- Faz parte do ecossistema do `Spring Framework`
- O `Spring` é um framework open source, Java, que facilita o desenvolvimento de aplicações.
- O `Spring Boot`, serve para criar aplicações, como APIs Rest, de forma simples.
- Para utilizarmos o `Spring Boot`, vamos utilizar o [Spring Initializr](https://start.spring.io/), que permite adicionar inicialmente um conjunto de dependências;
- Separação do código em camadas: `Entity, Repository, Service e Controller`;

### Criando um projeto Spring
- Para criamos o projeto inicial podemos utilizar o site [Spring Initializr](https://start.spring.io/)
- Nele podemos escolher o gerenciador de dependências, linguagem de programação, versão do `Spring Boot`
- Na parte do gerenciador de pacotes escolhemos a opção: `maven`
- Na parte de linguagem de programação, usamos o `Java`
- Em `Spring Boot`, escolhemos a versão do spring que vamos utilizar
- Em `Project Metadada`, vamos passar informações do projeto
	- Em `Group`, usamos um domínio, porém no sentido inverso, como por exemplo: `br.com.descomplica.projeto`
	- Em `Artifact`, é o nome que vamos dar ao nosso projeto
- Passando as duas informações acima, automaticamente será gerado um `Package name`
- Em `Packaging`, podemos manter o padrão `JAR`
- Depois podemos escolher a versão do Java disponível. Isso depende de qual versão da JDK está instalada em seu computador
- Ao lado direito, podemos adicionar as dependências inicias, que vão ser:
	- `Spring Web`
	- `Spring Data JPA`
	- `H2 Database`
	- `Spring Boot Dev Tools`
- Tendo terminado, podemos apenas apertar na opção `GENERATE`, assim um arquivo zipado, será baixo em seu computador;

### Entity
- Entidades, são classes Java que representam dentro da nossa API, toda a estrutura existente no banco de dados;
- Classe Java utilizada para representar uma Entidade no Banco de Dados;
- Pode ser codificada a partir de uma tabela, colunas e relacionamentos já existentes no BD (Mapeamento Objeto Relacional);
- Pode ser codificada para gerar a tabela, colunas e relacionamentos no banco de dados;
- Abaixo podemos ver um exemplo de uma `Entity`
```java
@Entity
@Table(name = "categoria")
public class Categoria {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "categoria_id")
	private Integer categoriaId;

	@Column(name = "categoria_nome")
	private String categoriaNome;

	@OneToMany(mappedBy = "categoria")
	@JsonManagedReference
	private List<Produto> produtoList;
}
```
- O `Spring`, determina que para definir que essa classe vai ser uma `Entity`, precisamos usar uma anotação (`@Entity`);
- A anotação `@Table`, define qual a tabela no banco de dados vai ser relacionada a classe na qual passamos essa anotação;
- A anotação `@Id`, define que o papel do atributo é ser a chave primária;
- A anotação `@Column`, define a qual coluna do banco de dados esse atributo diz respeito;
- A anotação `@GeneratedValue`, define quem vai ser responsável por gerar a chave incremental;
- A anotação `@OneToMany`, que define o relacionamento entre entidades;

### Repository
- O `repository` é uma interface que estende outras interfaces (JpaRepository, CrudRepository, etc.)
- A função do `repository` é disponibilizar os métodos de acesso a dados.
- O padrão é termos um `repository`, para cada `entity` que fará parte da nossa API;
- Para criar um `repository`, fazemos igual ao exemplo abaixo:
```java
public interface CategoriaRepository extends JpaRepository<Categoria, Int>{}
```
- Nota-se que passamos entre `<>`, o primeiro parâmetro o nome da `Entity` a qual esse `repository`, vai estar ligado.
- E o segundo parâmetro, diz respeito ao tipo de dado que representa na `Entity`, a chave primária daquela entidade;

### Service
- Na camada `service`, temos a comunicação/intermediação entre a camada `controller` e a camada `repository`
- Nela também codificamos as regras de negócio da aplicação.
- O `service` é uma classe, e usamos uma anotação para definir que ela é um `service`.


### Controller
- Na camada `Controller` disponibilizamos os recursos/endpoints da nossa API Rest.
- Para isso, mapeamos o método HTTP, os `Path's` ou `URIs`, além de manipularmos/tratarmos as `Requests` e `Responses` HTTP.
- Abaixo temos um exemplo de um `controller`
```java
@RestController
@RequestMapping("/auth")
public class AuthController {

	@PostMapping("/registro")
	public Map<String, Object> registerHandle(@RequestBody user) {
		// Código para cadastrar um novo user
	}
		
}
```