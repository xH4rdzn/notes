___
### Estruturando a query nativa do extrato (Statement)
- Para podermos pegar os dados das entidades de *Transferências* e *Deposítos*, com ***SQL***, podemos usar o que chamamos de ***`UNION ALL`***, e podemos fazer seu uso como no exemplo abaixo:
```sql
SELECT 
	transfer_id as statement_id,
	"transfer" as type,
	transfer_value as statement_value,
	wallet_receiver_id as wallet_receiver,
	wallet_sender_id as wallet_sender,
	transfer_date_time as statement_date_time
FROM
	tb_transfers
UNION ALL
SELECT
	deposit_id as statement_id,
	"deposit" as type,
	deposit_value as statement_value,
	wallet_id as wallet_receiver,
	"" as wallet_sender
	deposit_date_time as statement_date_time
FROM
	tb_deposits		
```

### Incluindo a consulta de extrato no *WalletRepository*
- Agora no nosso repositório de *Wallets*, vamos adicionar o seguinte código:
```java

String SQL_STATEMENT = """
SELECT 
	transfer_id as statement_id,
	"transfer" as type,
	transfer_value as statement_value,
	wallet_receiver_id as wallet_receiver,
	wallet_sender_id as wallet_sender,
	transfer_date_time as statement_date_time
FROM
	tb_transfers
UNION ALL
SELECT
	deposit_id as statement_id,
	"deposit" as type,
	deposit_value as statement_value,
	wallet_id as wallet_receiver,
	"" as wallet_sender
	deposit_date_time as statement_date_time
FROM
	tb_deposits		

""";

@Query(value = SQL_STATEMENT, nativeQuery = true)
Page<StatementView> findStatements(UUID walletId, PageRequest pageRequest);
```

### Conhecendo o JPA Projections
- Quando fazemos uma união de tipos, podemos utilizar as *JPA Projections*.
- Para podermos utilizar esse recurso, dentro da nossa camada de *repository*, vamos criar outro pacote de *dto*, e dentro dele podemos fazer as nossas projeções, como o exemplo da ***StatementView***
```java
public interface StatementView {
	
	String getStatementId();
	String getType();
	BigDecimal getStatementValue();
	String getWalletReceiver();
	String getWalletSender();
	LocalDateTime getStatementDateTime();
}
```

### Incrementando a query para incluir filtro de wallet
- Quando estamos falando de extrato, estamos falando de uma determinada *Wallet*, nesse caso então precisamos adicionar os filtros *WHERE* em nossa *query*, deixando a da seguinte maneira:
```java
String SQL_STATEMENT = """
SELECT 
	BIN_TO_UUID(transfer_id) as statement_id,
	"transfer" as type,
	transfer_value as statement_value,
	BIN_TO_UUID(wallet_receiver_id) as wallet_receiver,
	BIN_TO_UUID(wallet_sender_id) as wallet_sender,
	transfer_date_time as statement_date_time
FROM
	tb_transfers
WHERE wallet_receiver = UUID_TO_BIN(?1) OR wallet_sender = UUID_TO_BIN(?1)
UNION ALL
SELECT
	BIN_TO_UUID(deposit_id) as statement_id,
	"deposit" as type,
	deposit_value as statement_value,
	BIN_TO_UUID(wallet_id) as wallet_receiver,
	"" as wallet_sender
	deposit_date_time as statement_date_time
FROM
	tb_deposits
WHERE
	wallet_receiver = UUID_TO_BIN(?1)

""";
```
- No ***MySQL*** o *UUID*, fica no formato binário, então usamos a função ***`UUID_TO_BIN(?1)`***
- Usamos a função `BIN_TO_UUID`, para converter um binário para **UUID**;
- E a função `UUID_TO_BIN`, para converter um **UUID** para binário

### Incluindo o countQuery para ter paginação e ordenação
- Quando usamos o *Query Method*, para termos a paginação e ordenação, precisamos acrescentar o atributo *countQuery*
```java
@Query(value = SQL_STATEMENT, countQuery = , nativeQuery = true)
Page<StatementView> findStatements(UUID walletId, PageRequest pageRequest);
```
- Então criamos a nossa *query* de count como no exemplo abaixo:
```sql
SELECT COUNT(*) FROM (
SELECT 
	transfer_id as statement_id,
	"transfer" as type,
	transfer_value as statement_value,
	wallet_receiver_id as wallet_receiver,
	wallet_sender_id as wallet_sender,
	transfer_date_time as statement_date_time
FROM
	tb_transfers
UNION ALL
SELECT
	deposit_id as statement_id,
	"deposit" as type,
	deposit_value as statement_value,
	wallet_id as wallet_receiver,
	"" as wallet_sender
	deposit_date_time as statement_date_time
FROM
	tb_deposits			
)
```
- Agora vamos criar outra constante para a nossa *query* de *count*
```java
String SQL_COUNT_STATEMENT = """ 
	SELECT COUNT(*) FROM 
	(
	""" + SQL_STATEMENT + """
	) as total
""";
```
- E agora passamos essa *query* para o nosso *countQuery*
```java
@Query(value = SQL_STATEMENT, countQuery = SQL_COUNT_STATEMENT, nativeQuery = true)
Page<StatementView> findStatements(UUID walletId, PageRequest pageRequest);
```

### Criando a API de extrato
- Dentro do nosso *WalletController*, vamos criar mais um endpoint:
```java
@GetMapping("/{walletId}/statements")
public ResponseEntity<StatementDTO> getStatements(@PathVariable("walletId") UUID walletId, @RequestParam(name = "page", defaultValue = 0) Integer page, @RequestParam(name = "pageSize", defaultValue = 0) Integer pageSize) {
	var statement = walletService.getStatements(walletId, page, pageSize);
	
	return ResponseEntity.ok(statement).build();
}
```
- Agora vamos criar o nosso `StatementDTO`
```java
public record StatementDTO(WalletDTO wallet,
List<StatementItemDTO> statements, PaginationDTO pagination) {}
```
- Agora em nosso `WalletDTO`, vamos criar o seguinte:
```java
public record WalletDTO(UUID walletId, String cpf, String name, String email, BigDecimal balance) {}
```
- Agora em nosso `StatementItemDTO`, vamos criar da seguinte maneira:
```java
public record StatementItemDTO(String statementId, String type, String literal, BigDecimal value, LocalDateTime datetime, StatementOperation operation) {}
```
- O `StatementOperation`, vamos criar um enum:
```java
public enum StatementOperation {
	
	CREDIT, DEBIT
	
}
```
- E o nosso `PaginationDTO`, criamos da seguinte maneira:
```java
public record PaginationDTO(Integer page, Integer pageSize, Long totalElements, Integer totalPages) {}
```
- Agora voltamos a nossa controller, e fazemos a importação do `StatementDTO`.
- Agora vamos implementar a lógica em nossa *Service*
```java
public StatementDTO getStatements(UUID walletId, Integer page, Integer pageSize) {
	
	walletRepository.findById(walletId)
		.orElseThrow(() -> new WalletNotFoundException("There is no wallet with this id"));
		
	var pageRequest = PageRequest.of(page, pageSize, Sort.Direction.DESC, "statement_date_time");	
	
	
	var statements = walletRepository.findStatements(walletId, pageRequest)
	.map(view -> mapToDTO(walletId, view));
	
	return new StatementDTO(
		new WalletDTO(wallet.getWalletId(), wallet.getCpf(), wallet.getName(), wallet.getEmail(), wallet.getBalance()),
		null,
		new PaginationDTO(statements.getNumber(), statements.getSize(), staatements.getTotalElements(), statements.getTotalPages())
	);
}


// Método mapToDTO
private StatementItemDTO mapToDTO(UUID walletId, StatementView view) {
	
	
	if(view.getType().equalsIgnoreCase("deposit")) {
		return new StatementItemDTO(
			view.getStatementId(),
			view.getType(),
			"money Deposit",
			view.getStatementValue(),
			view.getStatementDateTime(),
			StatementOperation.CREDIT
		)
	}
	
	
}
```