___
- Quando realizamos esse tipo de relacionamento, *sempre precisamos de uma tabela intermediária*;
- Para realizar esse tipo de relacionamento, vamos seguir o exemplo abaixo:
```java
@Entity
@Table(name = "tb_tags")
public class TagEntity {
	
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "tag_id")
	private Long id;
	
	@Column(name = "name", unique = true)
	private String name;
	
	// Construtor vazio
	
	// Getters e Setters
}
```
- Agora na entidade de `produtos`, vamos fazer o relacionamento:
```java
@Entity
@Table(name = "products")
public class ProductEntity {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "product_id")
	private Long productId;
	
	@Column(name = "product_name")
	private String productName;
	
	@Column(name = "price")
	private BigDecimal price;
	
	@ManyToMany
	@JoinTable(
		name = "tb_products_tags",
		uniqueConstraints = @UniqueConstraint(columnNames = {"product_id", "tag_id"}),
		joinColumns = @JoinColumn(name = "product_id")
		inverseJoinColumns = @JoinColumn(name = "tag_id")
	)
	private List<TagEntity> tags;
	
	// Construtor vazio
	
	// getters e setters
}
```
- A `@JoinTable` vai criar uma nova tabela fazendo a amarração entre as tabelas;
- Para ela precisamos passar um nome para a tabela que irá ser criada, no exemplo passamos o nome de `tb_products_tags`;
- E também precisamos passar o ***`joinColumns`***, como primeiro parâmetro precisamos passar a referência onde estamos criando o relacionamento, normalmente é o atributo **`id`**;
- E depois passamos a referência da outra tabela através do ***`inverseJoinColumns`***, que normalmente também é o ***`id`***;
- Usamos o `uniqueConstraints`, para que podemos ter um único índice na tabela associativa, em outras palavras, apenas uma referência pode estar associada a outra(Mesmo produto possuir a mesma tag mais de uma vez); 
