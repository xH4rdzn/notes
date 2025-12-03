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
```java
private final WalletRepository walletRepository;
```
- Agora precisamos garantir que a pessoa que está realizando a transferência, possui o saldo suficiente, para poder realizar a transferência.
```java
@Transactional
public void transferMoney(TransferMoneyDTO dto) {
	// Validando se as carteiras realmente existem.
	var sender = walletRepository.findById(dto.sender())
		.orElseThrow(() -> new WalletNotFoundExcepetion("Sender does not exists"));
		
	var receiver = walletRepository.findById(dto.receiver())
		.orElseThrow(() -> new WalletNotFoundExcepetion("Receiver does not exist"));
		
	if(sender.getBalance().compareTo(dto.value()) == -1) {
		throw new TransferException("Insufficient balance. You current balance is $ " + sender.getBalance());
	}
	
}
```
- Agora precisamos criar a nossa **TransferException**, como no exemplo abaixo:
```java
public class TransferException extends JBankException {

	private final String detail;
	
	public TransferException(String detail) {
		super(detail);
		this.detail = detail;
	}
	
	@Override
	public ProblemDetail toProblemDetail() {
		
		var pd = ProblemDetail.forStatus(HttpStatus.UNPROCESSABLE_ENTITY);
		
		pd.setTitle("Transfer not Allowed");
		pd.setDetail(detail);
		
		return pd;
	}

}
```
- Agora voltando para a nossa *service*, podemos continuar a implementação desse método:
```java
@Transactional
public void transferMoney(TransferMoneyDTO dto) {
	// Validando se as carteiras realmente existem.
	var sender = walletRepository.findById(dto.sender())
		.orElseThrow(() -> new WalletNotFoundExcepetion("Sender does not exists"));
		
	var receiver = walletRepository.findById(dto.receiver())
		.orElseThrow(() -> new WalletNotFoundExcepetion("Receiver does not exist"));
		
	if(sender.getBalance().compareTo(dto.value()) == -1) {
		throw new TransferException("Insufficient balance. You current balance is $ " + sender.getBalance());
	}
	
	var transfer = new Transfer();
	transfer.setReciver(receiver);
	tranfer.setSender(sender);
	transfer.setTransferValue(dto.value());
	transfer.setTransferDateTime(LocalDateTime.now());
	
	sender.setBalance(sender.getBalance().subtract(dto.value()));
	receiver.setBalance(receiver.getBalance().add(dto.value()));
	walletRepository.save(sender);
	walletRepository.save(receiver);
	
	
}
```
- Nosso método de transferência está concluído, agora precisamos fazer uma modificação em nossa *entidade*. Então em nossa entidade de *Wallet*, pois é ela que pode ter operações em concorrência, vamos adicionar a seguinte regra ao final de seus atributos:
```java
@Version
private Long version;

// getters e setters para esse novo atributo.

```
- Essa anotação ajuda para podermos não ter dados inconsistentes, para caso de ocorrer operações em concorrência, em outras palavras mais de uma operação com a mesma entidade ao mesmo tempo.