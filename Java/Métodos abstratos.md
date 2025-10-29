___
- Como temos [[Classes abstratas]], podemos também ter *métodos abstratos*, para fazer apenas a declaração do método;
- Para ter um método abstrato, precisa estar em uma classe abstrata.
- Os métodos abstratos precisam ser implementados em todas as classes concretas que herdam de uma classe abstrata.
- Para criar um método abstrato, podemos fazer como no exemplo abaixo:
```java
// Classe abstrato
public abstract class NotaFiscal {

	// Método abstrato
	public abstract double calcularImpostos();
	
}
```