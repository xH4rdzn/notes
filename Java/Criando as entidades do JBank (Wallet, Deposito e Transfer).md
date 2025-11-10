___
- Após [[Iniciando o projeto JBank|iniciar o nosso projeto]], agora vamos criar as entidades necessárias para a nossa aplicação e realizar os relacionamentos entre essas entidades.
- Para isso vamos criar um *package* com o nome de `entities`
### Criando a entidade de Carteira (Wallet)
- Vamos criar o arquivo `Wallet` dentro do *package* e fazer da seguinte maneira:
```java
@Entity
@Table(name = "tb_wallets")
public class Wallet {
	
	@Id
	@GeneratedValue(strategy = GenerationType.UUID)
	private UUID walletId;
	
	@Column(name = "cpf", unique = true)
	private String cpf;
	
	@Column(name = "email", unique = true)
	private String email;
	
	@Column(name = "name")
	private String name;
	
	@Column(name = "balance")
	private BigDecimal balance;
	
}
```
- Os métodos *getters e setters*, só vamos criar após fazer os relacionamentos necessários.

### Criando a entidade de Transferência (Transfer)
- Dentro do mesmo pacote vamos criar o arquivo `Transfer`e criar a nossa entidade:
```java
@Entity
@Table(name = "tb_transfers")
public class Transfer {
	
	@Id
	@GeneratedValue(strategy = GenerationType.UUID)
	private UUID tranferId;
	
	
	@ManyToOne
	@JoinColumn(name = "wallet_receiver_id")
	private Wallet receiver;
	
	@ManyToOne
	@JoinColumn(name = "wallet_sender_id")
	private Wallet sender;
	
	@Column(name = "transfer_value")
	private BigDecimal transferValue;
	
	@Column(name = "transfer_date_time")
	private LocalDateTime transferDateTime;
	
}
```

### Criando a entidade de Depositos (Deposit)
- Ainda dentro do mesmo *package*, vamos criar o arquivo `Deposit`e fazer da seguinte maneira:
```java
@Entity
@Table(name = "tb_deposits")
public class Deposit {

	@Id
	@GeneratedValue(strategy= GenerationType.UUID)
	private UUID depositId;
	
	@ManyToOne
	@JoinColumn(name = "wallet_id")
	private Wallet wallet;
	
	@Column(name = "deposit_value")
	private BigDecimal depositValue;
	
	@Column(name = "deposit_date_time")
	private LocalDateTime depositDateTime;
	
	@Column(name = "ip_address)
	private String ipAddress;
}
```
- Agora basta gerarmos os construtores vazios e os métodos getters e setters para todas as entidades.
- Subimos o projeto para verificar se está tudo correto e verificamos no *Beekeeper* o nosso banco de dados.