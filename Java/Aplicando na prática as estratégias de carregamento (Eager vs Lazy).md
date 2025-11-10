___
- Para aplicar essas as estratégias de carregamento aplicamos elas em nossa entidade
- Como no exemplo abaixo que estamos aplicando o ***`FetchType.Lazy`*** na nossa entidade de `User`, em nosso relacionamento com a tabela `BillingAddress`
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
	
	@OneToOne(fetch = FetchType.LAZY)
	@JoinColumn(name = "billing_address_id")
	private BillingAddressEntity billingAddress;
```
- Dessa maneira os dados de `BillingAddress`só serão puxados do banco de dados quando eles forem utilizados, caso não for, só recebemos a informação da existência do relacionamento.

### Mapeamento Unidirecional vs Bidirecional
- Quando temos um mapeamento bidirecional, podemos ter um *loop infinito*;
- O mapeamento bidirecional é quando as duas entidades tem referência uma para outra.
- Usamos esse mapeamento quando uma entidade precisa chegar na outra e vice-versa
- O mapeamento unidirecional é quando só existe referência em uma entidade.
- No lado mais fraco do relacionamento podemos cortar o mapeamento.

### FetchType.EAGER
- Quando queremos que retorne todos os dados na primeira chamada.
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
	
	@OneToOne(fetch = FetchType.EAGER)
	@JoinColumn(name = "billing_address_id")
	private BillingAddressEntity billingAddress;
```