___
### Aplicando a estratégia de cascade
- Para aplicar o `cascade`, ela é aplicada na anotação do relacionamento, como é demonstrado no exemplo abaixo:
```java
@Entity
@Table(name = "tb_users")
public class UserEntity {

	@Id
	@Column(name = "user_id")
	@GeneratedValue(strategy = GenerationType.UUID)
	private UUID userId;

	@Column(name = "full_name")
	private String fullName;
	
	@OneToOne(fetch = FetchType.EAGER, cascade= CascadeType.ALL)
	@JoinColumn(name = "billing_address_id")
	private BillingAddressEntity billingAddress;
```

### Ajustando o código para o novo formato
- Dessa maneira podemos mudar a nossa `service`, para interagir apenas com o repositório de `User`, pois ele vai cascatear as operações de acordo com o que foi configurado.
- No caso o tipo `ALL`, ele cascateá todas as operações;

### Usando mais de um tipo de cascade
- Para podermos usar mais de um tipo, caso não queiramos usar o tipo `ALL`, podemos fazer da seguinte maneira:
```java
@Entity
@Table(name = "tb_users")
public class UserEntity {

	@Id
	@Column(name = "user_id")
	@GeneratedValue(strategy = GenerationType.UUID)
	private UUID userId;

	@Column(name = "full_name")
	private String fullName;
	
	@OneToOne(fetch = FetchType.EAGER, cascade = { CascadeType.PERSIST, CascadeType.REMOVE})
	@JoinColumn(name = "billing_address_id")
	private BillingAddressEntity billingAddress;
```