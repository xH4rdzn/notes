___
### Definindo o contrato da API através de DTO
- Criamos os *DTOs*, para evitar de usar a entidade diretamente.
- Com isso conseguimos blindar a nossa aplicação e fazer trafegar apenas os dados desejados.
- Para criar um *DTO*, podemos fazer como no exemplo abaixo:
```java
public record CreateUserDTO(String fullName, String address, String number, String complement) {}
```

### Criando a API @PostMapping
- Agora em nossa `controller`, injetamos a dependência da `service`e podemos fazer como no exemplo abaixo:
```java

	private final UserService userService;
	
	public UserController(UserService userService) {
		this.userService = userService;
	}

@PostMapping
public ResponseEntity<Void> createUser(@RequestBody CreateUserDTO dto) {
	
	var user = userService.createUser(dto);
	
	
	return ResponseEntity.created(URI.create("/users/" + user.getUserId())).build();
}
```

### Implementando a lógica de persistências dos relacionamentos
- Agora em nossa `service`, podemos implementar a lógica para salvar os dados necessários.
- Fica atento sempre a lógica, no exemplo para cadastrar um usuário precisamos ter um endereço cadastrado, então primeiro salvamos o endereço e depois os dados do usuário. Exemplo:
```java
public UserEntity createUser(CreateUserDTO dto) {
	
	var billingAddress = new BillingAddressEntity();
	billingAddress.setAddress(dto.address());
	billingAddress.setNumber(dto.number());
	billingAddress.setComplement(dto.complement());
	
	var savedBillingAddress = billingAddressRepository.save(billingAddress);
	
	
	var user = new UserEntity();
	user.setFullName(dto.fullName());
	user.setBillingAddress(savedBillingAddress);
	
	return userRepository.save(user);
}
```