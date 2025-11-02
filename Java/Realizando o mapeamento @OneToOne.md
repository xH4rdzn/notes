___
- Para realizar o relacionamento de um para um, usamos a anotação `@OneToOne`, então como demonstrado no exemplo abaixo:
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
	
	@OneToOne
	@JoinColumn(name = "billing_address_id")
	private BillingAddressEntity billingAddress;
	
	
	// Construtor vazio, getters e setters de todos os atributos
	

}


// Entidade de endereço de combrança

@Entity
@Table(name = "tb_billing_addrress")
public class BillingAddress {
	
	@Id
	@Column(name = "billing_address_id")
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long billingAddressId;
	
	@Column(name = "address")
	private String address;
	
	@Column(name = "number")
	private String number;
	
	@Column(name = "complement")
	private String complement;
	
	@OneToOne(mappedBy = "billingAddress")
	private UserEntity user;
	
	// Construtor Vazio, getters e setters de todos os atributos;
	
}
```
- A anotação ***`@JoinColumn`*** serve para criar mais uma coluna na tabela principal que vai conter a chave estrangeira do relacionamento.
- Na tabela mais fraca do relacionamento, precisamos usar a anotação ***`@OneToOne`*** também, mas nela passamos a propriedade `mappedBy`e como valor ela recebe o nome do atributo que vai conter essa chave;