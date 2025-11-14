___
- Para podermos fazer essa funcionalidade, vamos criar um endpoint do tipo `POST`, em nossa controller de `WalletController` como no exemplo abaixo:
```java
@PostMapping(path = "/{walletId}/deposits")
public ResponseEntity<Void> depositMoney(@PathVariable("walletId") UUID walletId, @RequestBody @Valid DeposityMoneyDTO dto) {

	 walletService.deposityMoney(walletId, dto);

}
```
- Em nosso *DTO*, vamos por os dados necessário para criar um deposito, como no exemplo abaixo:
```java
public record DepositMoneyDTO(@NotNull @DecimalMin("1.00") BigDecimal value) {}
```
- Agora o que precisamos fazer é a lógica dentro da nossa camada de `service`
```java
public void depositMoney(UUID walletId, DepositMoneyDTO dto) {}
```
- Como temos que fazer duas operações conjuntas, inserir os dados na tabela de depósitos e atualizar o valor da carteira, podemos usar a anotação `@Transactional`, para caso de erro em uma das operações, ele não execute nenhum operação.
- Então anotamos o nosso método na `service`
```java
@Transactional
public void depositMoney(UUID walletId, DepositMoneyDTO dto) {

	var wallet = walletRepository.findById(walletId).orElseThrow(() -> new WalletNotFoundExcepetion("there is no wallet with this id"));
	
	var deposit = new Deposit();
	deposit.setWallet(wallet)
	deposit.setDepositValue(dto.value());
	deposit.setDepositDateTime(LocalDateTime.now());
	deposit.setIpAddress(ipAddress);**
	
}
```
- Para recuperar o `ipAddress`, em nossa controller, vamos adicionar a seguinte linha em nosso método:
```java
@PostMapping(path = "/{walletId}/deposits")
public ResponseEntity<Void> depositMoney(@PathVariable("walletId") UUID walletId, @RequestBody @Valid DeposityMoneyDTO dto, HttpServletRequest servletRequest) {

	 walletService.deposityMoney(walletId, dto, servletRequest.getAttribute("x-user-ip").toString());

}
```
- Agora também podemos criar a nossa exceção de `WalletNotFoundException`, como no exemplo abaixo:
```java
public class WalletNotFoundException extends JBankException {
	
	private final String detail;
	
	
	public WalletNotFOundExcepetion(String detail) {
		super(detail);
		this.detail = detail;
	}

	@Override
	public ProblemDetail toProblemDetail() {
		var pd = ProblemDetail.forStatus(HttpStatus.NOT_FOUND);
		
		pd.setTitle("Wallet not Found");
		pd.setDetail(detail);
		
		return pd;
	}
}
```
- Agora podemos salvar :
```java
@Transactional
public void depositMoney(UUID walletId, DepositMoneyDTO dto) {

	var wallet = walletRepository.findById(walletId).orElseThrow(() -> new WalletNotFoundExcepetion("there is no wallet with this id"));
	
	var deposit = new Deposit();
	deposit.setWallet(wallet)
	deposit.setDepositValue(dto.value());
	deposit.setDepositDateTime(LocalDateTime.now());
	deposit.setIpAddress(ipAddress);
	
	deposityRepository.save(deposit);
	wallet.setBalance(wallet.getBalance().add(dto.value()));
	walletRepository.save(wallet);
	
}
```
- Agora podemos finalizar o retorno em nossa `controller`
```java
@PostMapping(path = "/{walletId}/deposits")
public ResponseEntity<Void> depositMoney(@PathVariable("walletId") UUID walletId, @RequestBody @Valid DeposityMoneyDTO dto, HttpServletRequest servletRequest) {

	 walletService.deposityMoney(walletId, dto, servletRequest.getAttribute("x-user-ip").toString());
	 
	 return ResponseEntity.ok().build();

}
```
- Quando tivermos operações casadas em duas ou mais tabelas é bom usarmos a anotação `@Transactional`, para caso de uma exceção ou erro acontecer, ela não inserir nenhum dado em nosso banco de dados.