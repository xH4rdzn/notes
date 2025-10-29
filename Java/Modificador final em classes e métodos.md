___
- Com o modificador ***`final`*** em classes, conseguimos fazer com que ela não possa ser herdada por nenhuma outra classe;
```java
public final class ContaEspecial {
	
	// Implementação
	
}
```
- Essa classe ***`ContaEspecial`***, não pode ser herdada por nenhuma outra classe;
- Já em métodos podemos utilizar o modificador ***`final`***, para que ele não possa ser sobrescrito;
```java
public final void depositar(double valorDeposito) {
	// Implementação
}
```
- Podemos implementar o ***`final`*** em um método que já foi sobrescrito, que queremos que aquela seja a sua última implementação.
- Usamos para métodos que retornam informações sensíveis;