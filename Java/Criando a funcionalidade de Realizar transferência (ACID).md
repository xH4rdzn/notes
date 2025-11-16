___
- ***`ACID`*** -> É uma sigla para uma operação de transação dentro do banco de dados que é -> Atômica, Coerente, Isolada e Durável.
- Para isso vamos precisar criar um endpoint do tipo `POST`, então em nosso controller de transferências , podemos criar como no exemplo abaixo:
```java
// TransferController.java
public ResponseEntity<Void> transfer(@RequestBody @Valid TransferMoneyDTO dto) {}
```
- Agora precisamos do nosso `repository`e `service`
```java
@Service
public class TransferService {}
```
- `repository`
```java
public interface TransferRepository extends JpaRepository<Transfer, UUID> {}
```
- Agora em nossa `Service`, vamos injetar o nosso `repository`
- E em nossa `Controller`, vamos injetar a nossa `Service`;
- Então no método do nosso `Controller`, vamos precisar criar um *`DTO`*, que demos o nome de `TransferMoneyDTO`, para isso vamos criar ele abaixo:
```java
public record TransferMoneyDTO(@NotNull UUID sender,@NotNull @DecimalMin("0.01") BigDecimal value,@NotNull UUID receiver) {}
```
- Agora em nosso método, precisamos chamar o método da nossa `Service`, como no exemplo abaixo:
```java
// TransferController.java
public ResponseEntity<Void> transfer(@RequestBody @Valid TransferMoneyDTO dto) {

	transferService.transferMoney(dto);

	return ResponseEntity.ok().build();
}
```
- Agora precisamos implementar a lógica dentro do nosso `service`;
```java
@Transactional
public void transferMoney(TransferMoneyDTO dto) {
	// Validando se as carteiras realmente existem.
	var sender = walletRepository.findById(dto.sender())
		.orElseThrow(() -> new WalletNotFoundExcepetion("Sender does not exists"));
		
	var receiver = walletRepository.findById(dto.receiver())
		.orElseThrow(() -> new WalletNotFoundExcepetion("Receiver does not exist"));	
}
```
- **Como vamos ter que interagir com a tabela de *wallets*, precisamos injetar o seu repositório também.**
- 