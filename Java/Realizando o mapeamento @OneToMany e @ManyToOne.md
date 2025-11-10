___
### Criando a OrderEntity
```java
@Entity
@Table(name = "tb_orders")
public class OrderEntity {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "order_id")
	private Long orderId;
	
	@Column(name = "total")
	private BigDecimal total;
	
	@Column(name = "order_date")
	private LocalDateTime orderDate;
	

	// construtor vazio 
	
	// getters e setters
}
```

### Criando a OrderItemEntity
```java
@Entity
@Table(name = "tb_order_item")
public class OrderItemEntity {

	@Column(name = "sale_price")
	private BigDecimal salePrice;
	
	
	@Column(name = "quantity")
	private integer quantity;
	
	// construtor vazio
	
	// getters e setters
}
```

### Criando a ProductEntity
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
	
	// Construtor vazio
	
	// getters e setters
}
```

### Chave composta com @EmbeddedId na OrderItemEntity
- Essa tabela precisa estar relacionada à `ProductEntity`e a `OrderEntity`, então aqui vamos ter uma chave composta.
- Para fazermos isso vamos ter que criar uma nova classe, nesse caso a `OrderItemId`, e vamos anotar ela com o `@Embeddable`, como é demonstrado no exemplo abaixo:
```java
@Embeddable
public class OrderItemId {

	@ManyToOne
	@JoinColumn(name = "order_id")
	private OrderEntity order;
	
	@ManyToOne
	@JoinColumn(name = "product_id")
	private ProductEntity product;
	
	// construtor vazio
	
	// getters e setters

}
```
- Agora na nossa entidade de `OrderItemEntity`, vamos adicionar o seguinte campo e anotar ele com `@EmbeddedId`
```java
@Entity
@Table(name = "tb_order_item")
public class OrderItemEntity {

	@EmbeddedId
	private OrderItemId id;

	@Column(name = "sale_price")
	private BigDecimal salePrice;
	
	
	@Column(name = "quantity")
	private integer quantity;
	
	// construtor vazio
	
	// getters e setters
}
```

### Criando @ManyToOne entre OrderEntity e UserEntity
- Na nossa entidade de `OrderEntity`, vamos adicionar:
```java
@Entity
@Table(name = "tb_orders")
public class OrderEntity {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "order_id")
	private Long orderId;
	
	@Column(name = "total")
	private BigDecimal total;
	
	@Column(name = "order_date")
	private LocalDateTime orderDate;
	
	@ManyToOne
	@JoinColumn(name = "user_id")
	private UserEntity user;
	

	// construtor vazio 
	
	// getters e setters
}
```

### Criando @OneToMany entre OrderEntity e OrderItemEntity
- Ainda na nossa entidade `OrderEntity`, vamos adicionar o relacionamento com a tabela `OrderItemEntity`
```java
@Entity
@Table(name = "tb_orders")
public class OrderEntity {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "order_id")
	private Long orderId;
	
	@Column(name = "total")
	private BigDecimal total;
	
	@Column(name = "order_date")
	private LocalDateTime orderDate;
	
	@ManyToOne
	@JoinColumn(name = "user_id")
	private UserEntity user;
	
	@OneToMany(mappedBy = "id.order", cascade = CascadeType.ALL)
	private List<OrderItemEntity> items;

	// construtor vazio 
	
	// getters e setters
}
```