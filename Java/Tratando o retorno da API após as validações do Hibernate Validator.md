___
- Para podermos tratar os erros de validações, normalmente ele retorna uma `MethodArgumentNotValidException`, desta maneira para podermos tratar de maneira global essa exceção em nosso `GlobalExceptionHandler`, podemos fazer o seguinte:
```java
@ExceptionHandler(MethodArgumentNotValidException.class)
public ProblemDetail handleMethodArgumentNotValidException(MethodArgumentNotValidException e) {
	var invalidParams = e.getFieldErrors()
		.stream()
		.map(fe -> new InvalidParamDTO(fe.getField(), fe.getDefaultMessage()))
		.toList();
		
		
	var pd = ProblemDetail.forStatus(400);
		
	pd.setTitle("Invalid request parameters");
	pd.setDetail("There is invalid fields on the request");
	pd.setProperty("invalid-params", invalidParams);
	
	return pd;
}
```
- Usamos um *DTO*, para podermos formatar os dados
```java
public record InvalidParamDTO(String field, String reason){}
```
- Desta maneira já temos um retorno mais amigável e dentro do padrão;
- E ele sempre vai retornar os campos que estão inválidos, independente da quantidade;