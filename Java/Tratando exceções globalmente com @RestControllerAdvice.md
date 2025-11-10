___
- Para podermos tratar as exceções de forma global, vamos ter que criar um `@RestControllerAdvice`, então para isso dentro do nosso *package exception*, vamos criar o `GlobalExcepetionHandler`;
- Dentro dele vamos fazer o seguinte:
```java
@RestControllerAdvice
public class GlobalExceptionHandler {

	@ExceptionHandler(WalletDataAlreadyExistsException.class)
	public ProblemDetail handleWalletDataAlreadyExistsException(WalletDataAlreadyExistsException e) {
		var pd = ProblemDetail.forStatus(422);
		
		pd.setTitle("Wallet data already exists");
		pd.setDetail(e.getMessage());
		
		
		return pd;
	}

}
```


### Boas prática de tratamento de exceções
- Como estamos tratando as exceções de maneira global a cada exceção nova, vamos precisar criar um novo método como no exemplo acima.
- Uma boa prática é acessar a exceção pai, neste caso a `JBankException`e criar o seguinte método:
```java
public ProblemDetail toProblemDetail() {
	var pd = ProblemDetail.forStatus(500);
	
	pd.setTitle("JBank Internal Server Error");
	pd.setDetail("Contact JBank support");
	
	return pd;
}
```
- Agora desta maneira a cada exceção específica, podemos sobrescrever o esse método fazendo a tratativa para aquela exceção.
- Desta maneira em nosso `@RestControllerAdvice`, podemos deixar o nosso handler global da seguinte maneira:
```java
@RestControllerAdvice
public class GlobalExceptionHandler {
	

	@ExceptionHandler(JBankException.class)
	public ProblemDetail handleJBankException(JBankException e) {
		return e.toProblemDetail();
	}

}
```