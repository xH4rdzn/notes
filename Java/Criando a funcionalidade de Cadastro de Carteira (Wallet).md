___
- No *package Controllers*, vamos criar o arquivo `WalletController` e nela vamos fazer o seguinte:
```java
@RestController
@RequestMapping(path = "/wallets")
public class WalletController {

}
```
- Precisamos criar a nossa `service`e a nosso `repository`
```java
// Service
@Service
public class WalletService {

	private final WalletRepository walletRepository;
	
	public WalletService(WalletRepository walletRepository) {
		this walletRepository = walletRepository;
	}
	
}


// Repository
public interface WalletRepository extends JpaRepository<Wallet, UUID> {}
```
- Agora em nossa `controller`,podemos injetar a dependência da `service`
```java
@RestController
@RequestMapping(path = "/wallets")
public class WalletController {

	private final WalletService walletService;
	
	public WalletController(WalletService walletService) {
		this.walletService = walletService;
	}
	
	@PostMapping
	public ResponseEntity<Void> createWallet(@RequestBody CreateWalletDTO dto) {
		
		walletService.createWallet(dto);
		
		return ResponseEntitu.created();
		
	}
}
```
- Agora desta maneira, podemos criar o nosso *DTO*
```java
public record CreateWalletDTO(String cpf, String email, String name) {}
```
- Agora precisamos implementar esse método `createWallet`dentro da nossa `Service`
```java
// WalletService

public Wallet createWallet(CreateWalletDTO dto) {
	walletRepository.findByCpfOrEmail(dto.cpf(), dto.email());
}
```
- Como o método `findByCpfOrEmail`, não existe em nosso repositório, precisamos fazer a implementação dele, então em nosso repositório adicionamos o método:
```java
public interface WalletRepository extends JpaRepository<Wallet, UUID> {

	Optional<Wallet> findByCpfOrEmail(String cpf, String email);

}
```
- Agora podemos voltar ao nosso `service`e continuar a implementação do método de criação de novas carteiras
```java
// WalletService

public Wallet createWallet(CreateWalletDTO dto) {
	var wallet = walletRepository.findByCpfOrEmail(dto.cpf(), dto.email());
	
	if(wallet.isPresent()) {
		
	}
	
}
```
- Agora precisamos criar as nossas exceções, para isso vamos criar um novo *package* com o nome de `exceptions`e nele vamos criar as nossas exceções personalizadas;
- Nesse caso vamos criar uma exceção pai e depois várias exceções filhas. Começando pela exceção pai, todas as exceções vão passar por ela. Para criar ela vamos fazer como no exemplo abaixo:
```java
public abstract class JbankException extends RuntimeException {

	public JBankExcepetion(String message) {
		super(message);
	}
	
	public JBankException(Throwable cause) {
		super(cause);
	}

}
```
- Por se tratar de uma classe abstrata não podemos fazer uma instância dela, para isso precisamos criar exceções filhas para poder herdar o comportamento dela e fazer a sua instância.
- Agora como a exceção se trata de uma carteira que já existe, podemos fazer a seguinte exceção:
```java
public WalletDataAlreadyExistsException extends JBankException{

	public WalletDataAlreadyExistsException(String message) {
		super(message);
	}
	
}
```
- Voltando para o nosso `service`, podemos fazer uma nova instância dessa exceção:
```java
// WalletService

public Wallet createWallet(CreateWalletDTO dto) {
	var walletDb = walletRepository.findByCpfOrEmail(dto.cpf(), dto.email());
	
	if(walletDb.isPresent()) {
		throw new WalletDataAlreadyExistsException("CPF or Email already exists");
	}
	
	var wallet = new Wallet();
	wallet.setBalance(BigDecimal.ZERO);
	wallet.setName(dto.name());
	wallet.setCpf(dto.cpf());
	
	return walletRepository.save(wallet);
}
```
- Agora voltando para a nossa `controller`, podemos continuar a implementação do método:
```java
@RestController
@RequestMapping(path = "/wallets")
public class WalletController {

	private final WalletService walletService;
	
	public WalletController(WalletService walletService) {
		this.walletService = walletService;
	}
	
	@PostMapping
	public ResponseEntity<Void> createWallet(@RequestBody CreateWalletDTO dto) {
		
		var wallet = walletService.createWallet(dto);
		
		return ResponseEntitu.created(URI.create("/wallets/" + wallet.getWalletId().toString())).build();
		
	}
}
```