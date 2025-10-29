___
- Polimorfismo conceitualmente é a capacidade de um objeto ser enxergado de diferentes formas.
- Para podermos fazer isso, usamos a classe mais genérica da cadeia de herança, uma vez que ela não perde o tipo da super classe.
- Como demonstrado no exemplo abaixo que passamos o tipo ***Conta***, para o método ***`transferir`***
```java
public void transferir(Conta contaOrigem, Conta contaDestino, double valorTransferencia) {
	
	// Implementação
	
}
```
- Desta maneira não precisamos fazer várias sobrecargas de métodos para poder receber cada tipo de conta, **iria ter muita duplicidade de código**;
- Usando o tipo ***Conta***, que é a classe mais genérica, podemos fazer apenas um método.
- Mas dependendo do tipo de conta que é passado como argumento seus métodos possuem comportamentos diferentes.