___
- Todo o código que colocarmos no `finally`, será executado, independente de ocorrer o lançamento de exceções ou não.
- Usamos como no exemplo abaixo:
```java
try {
	// Código
} catch(ArithimeticExpection e) {
	// Código
} finally {
	// Código que sempre vai ser executado
}
```
