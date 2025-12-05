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