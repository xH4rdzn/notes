___
- No *Java*, podemos criar as nossas próprias exceções;
- Para podermos criar a nossa exceção, devemos criar uma classe, com exatamente o nome da exceção que queremos criar, como por exemplo: **SaldoInsuficienteException**;
- E dentro desse arquivo, podemos fazer como no exemplo abaixo:
```java
public class SaldoInsuficienteException extends RunTimeException {
	public SaldoInsuficienteException(String message) {
		super(message)
	}
}
```
- Agora podemos usar essa Exception:
```java
if(conta.saldo < valor) {
	throw new SaldoInsuficienteException("Slado Insuficiente");
}
```