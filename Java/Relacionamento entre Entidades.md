___
### Relacionamento entre Entidades
- No `Spring Boot`, os relacionamentos são identificados com anotações
- São exemplos dessas anotações: `@OneToOne`, `@OneToMany`,`@ManyToOne` e `@ManyToMany`
- Podemos ter um relacionamento bidirecional;

### Relacionamento One-To-One
- É o relacionamento 1:1 (um para um);
- Nesse relacionamento, a exemplo do que aprendemos em Banco de dados, temos uma instância de uma Entidade se relacionando com apenas uma instância de outra Entidade;
- Um exemplo de um relacionamento `One-To-One` são:
	- *Uma pessoa só ter um endereço e esse endereço só pode pertencer a essa pessoa*;
	- *Uma pessoa só pode ter um número de telefone e esse número só pode pertencer a essa pessoa.*
- Abaixo vemos um exemplo de como criar um relacionamento `One-To-One`
```java
// Entidade Pessoa

@Entity
@Table(name = "pessoa")
class Pessoa {
	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	@Column(name = "id")
	private Long id;


	@OneToOne
	@JoinColumn(name = "endereco_id", referencedColumnName = "id")
	private Endereco endereco;
}

// Entidade Endereco

@Entity
@Table(name = "endereco")
class Endereco {
	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	@Column(name = "id")
	private Long id;

	@OneToOne(mappedBy = "endereco")
	private Pessoa pessoa;
}
```
- A anotação `@OneToOne` é utilizada para indicar o relacionamento entre as entidades;
- Enquanto a anotação `@JoinColumn`, define as colunas que representam a chave primária e a chave estrangeira no banco de dados.
- A anotação bidirecional, utilizando `mappedBy`, permite navegar a relação tanto da entidade Pessoa para Endereço quanto de Endereço para Pessoa, tornando o acesso aos dados mais flexível.

### Relacionamento One-To-Many
- É o relacionamento 1:N (Um para Muitos);
- Uma instância de uma Entidade se relaciona com várias instâncias de outra Entidade;
- Um exemplo de relacionamento `One-To-Many` são:
	- *Uma editora publica vários livros (e o livro é publicado por apenas uma editora)*
	- *Uma pessoa possui alguns números de telefone (e esses telefones pertencem a essa única pessoa)*;
- Abaixo vemos um exemplo de como criar um relacionamento `One-To-Many`:
```java
// Entidade Editora

@Entity
@Table(name = "editora")
class Editora {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "id")
	private Integer id;


	@OneToMany(mappedBy = "editora")
	private Set<Livro> livros;
}

// Entidade Livro

@Entity
@Table(name = "livro")
class Livro {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "id")
	private Integer id;


	@ManyToOne
	@JoinColumn(name = "id_editora", referencedColumnName = "id" )
	private Editora editora;
}
```
- No mapeamento `One-To-Many`, a entidade com a anotação `@OneToMany` precisa de uma coleção para armazenar as instâncias relacionadas. A anotação `@ManyToOne` no lado inverso indica que várias instâncias podem estar ligadas a uma única instância da outra entidade.