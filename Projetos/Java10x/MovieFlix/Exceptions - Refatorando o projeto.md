___
- Dentro do nosso projeto vamos criar um novo pacote com o nome de *`exceptions`*;
- Agora vamos criar uma classe com o nome `UsernameOrPasswordInvalidException`, e dentro dela vamos fazer o seguinte:
```java
public class UsernameOrPasswordInvalidException extends RuntimeException {

	public UsernameOrPasswordInvalidException(String message) {
		super(message);
	}

}
```
- Agora em nosso `AuthController`, vamos envolver o método de *`login`* em um bloco ***`try-catch`***, como no exemplo abaixo:
```java
@PostMapping("/login")
public ResponseEntity<LoginResponse> login(@RequestBody LoginRequest request) {
	try {
		// Código para Login
	} catch(BadCredentialsException e) {
		throw new UsernameOrPasswordInvalidException("Usuário ou senha inválido");
	}
}
```
- Agora para podermos tratarmos essas exceções, dentro da pasta *config*, vamos criar a classe `ApplicationControllerAdvice`, e dentro dela vamos fazer o seguinte:
```java
@RestControllerAdvice
public class ApplicationControllerAdvice {
	
	@ExceptionHandler(UsernameOrPasswordInvalidException.class)
	@ResponseStatus(HttpStatus.BAD_REQUEST)
	public String handleNotFoundException(UsernameOrPasswordInvalidExcepetion ex) {
		return ex.getMessage();
	}
}
```
- Agora em nosso `SecurityConfig`, vamos adicionar uma configuração no método `securityFilterChain`, que é a linha abaixo:
```java
// Deve estar dentro do authorizeHttpRequests
	.dispatcherTypeMatchers(DispatcherType.ERROR).permitAll()
```
- Para podermos validarmos, vamos fazer o uso das anotações para validação dos dados de entrada.
- Voltando para o nosso `ApplicationControllerAdvice`, vamos adicionar outro método:
```java
@ExceptionHandler(MethodArgumentNotValidException.class)
@ResponseStatus(HttpStatus.BAD_REQUEST)
public Map<String, String> handleArgumentNotValidExcepetion(MethodArgumetNotValidEception ex) {
	Map<String, String> erros = new HashMap<>();
	ex.getBidingResult().getAllErrors().forEach((error) ->
		errors.put(((FieldError) error).getField(), error.getDefaultMessage())
	);
	return errors;
	
}
```