___
### Conhecendo o @ResponseStatus
- Podemos devolver um *statusCode* diferente para as exceções, para isso podemos anotar ela com o `@ResposeStatus`, como é demonstrado no exemplo a seguir:
```java
@ResponseStatus(HttpStatus.UNPROCESSABLE_ENTITY)
public class WalletDataAlreadyExistsException extends JBankException {

	public WalletDataAlreadyExistsException(String message) {
		super(message);
	}

}
```

### Criando um @ExceptionHandler
- Dentro da nossa `controller`, podemos adicionar a anotação `@ExceptionHandler`e fazer como é demonstrado no exemplo abaixo:
```java
@ExceptionHandler(WalletDataAlreadyExistsException.class)
public ProblemDetail handleWalletDataAlreadyExistsException(WalletDataAlreadyExistsException e) {
	var pd =  ProblemDetail.forSatus(422);
	pd.setTitle("Wallet data already exists");
	
	pd.setDetail(e.getMessage())
	return pd;
}
```