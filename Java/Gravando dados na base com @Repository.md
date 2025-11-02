___
### Criando endpoint *@PostMapping*

- Para fazer a gravação de registros no banco de dados em uma API, usamos o método HTTP do tipo ***`POST`***
- Então para criar um endpoint precisamos de um *`controller`*, e nele que definimos os métodos HTTP e as rotas
- Para criarmos um `controller`e uma requisição do tipo `POST`, podemos fazer como no exemplo abaixo:
```java
@RestController
@RequestMapping(path = "/users")
public class UserController {}
```
- Para podermos usarmos a nossa `controller` precisamos de uma camada intermediária entre o `repository`e o `controller`, essa camada é a `service`, para criarmos um `service`, podemos seguir com o exemplo abaixo:
```java
@Service
public class UserService {}
```
- Nessa camada injetamos a dependência do `repository`, para isso injetamos essa dependência via construtor, como é demonstrado no exemplo abaixo:
```java
@Service
public class UserService {

	private final UserRepository userRepository;
	
	public UserService(UserRepository userRepository) {
		this.userRepository = userRepository;
	}

}
```
- Agora voltamos para a nossa `controller`e injetamos a dependência de `service`, que fazemos igual no exemplo acima
```java
@RestController
@RequestMapping(path = "/users")
public class UserController {

	private final UserService userService;
	
	public UserController(UserService userService) {
		this.userService = userService;
	}

}
```
- E agora podemos criar um *endpoint* do tipo `POST`
```java
@RestController
@RequestMapping(path = "/users")
public class UserController {

	private final UserService userService;
	
	public UserController(UserService userService) {
		this.userService = userService;
	}

	@PostMapping
	public ResponseEntity<Void> createUser() {}

}
```

### Conhecendo o conceito de DTO
- Uma boa prática quando estamos trabalhando com banco de dados é não deixarmos a nossa `Entity` totalmente exposta na nossa `controller`;
- Sendo assim, só precisamos expor os dados que queremos receber, para isso usamos os *DTO*;
- Os *DTO* são ***Data Transfer Object*** é um objeto que usamos para fazer a transferência de dados entre camadas;
- Para criar um *DTO*, podemos seguir com o exemplo abaixo:
```java
public record CreateUserDTO(String name, Long age) {}
```
- Criamos ele como um ***`record`*** e passamos como parâmetros apenas os dados que vamos receber;

### Gravando na base de dados
- Agora voltando ao nosso `service`, implementamos o método, e passamos o nosso *DTO*, como no exemplo abaixo:
```java
public UserEntity createUser(CreteUserDTO dto) {
	
	return null;
}
```
- Como precisamos retornar uma `UserEntity`e estamos recebendo um `createUserDTO`, precisamos fazer a conversão desses dados, para isso podemos seguir como no exemplo abaixo:
```java
public UserEntity createUser(CreteUserDTO dto) {
	
	var entity = new UserEntity();
	entity.setName(dto.name());
	entity.setAge(dto.age());
	entity.setCreatedAt(LocalDateTime.now());
	
	return userRepository.save(entity);
}
```
- Agora voltamos a nossa `controller`, e podemos continuar o método que usamos a anotação `@PostMapping`, como no exemplo abaixo:
```java
@RestController
@RequestMapping(path = "/users")
public class UserController {

	private final UserService userService;
	
	public UserController(UserService userService) {
		this.userService = userService;
	}

	@PostMapping
	public ResponseEntity<Void> createUser(@RequestBody CreateUserDTO dto) {
	
		var user = userService.createUser(dto);
		
		return ResponseEntity.created(URI.create("/users" + user.getUserId())).build();
	}

}
```