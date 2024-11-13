___
- Iteirar ou percorrer os valores de um array;
- Em Java temos várias maneiras de fazer isso, mas a mais comum é utilizando a [Estrutura de repetição for](./Estrutura%20de%20repetição%20for.md);
- Fazemos isso da seguinte maneira:
```java
public class Calculadora {
	static double calcularMedia(int[] numeros) {
		int total = 0;

		for(int i = 0; i < 5; i++) {
			total += numeros[i];
		}

		return (double) total / 5;
		
	}
}
```
- *Nota-se que o nosso método não está dinâmico, pois o tamanho do array pode variar*; 
- Para alterar isso podemos usar um método do `array`, chamada de `length`, então podemos alterar o exemplo acima para:
```java
public class Calculadora {
	static double calcularMedia(int[] numeros) {
		int total = 0;

		for(int i = 0; i < numeros.length; i++) {
			total += numeros[i];
		}

		return (double) total / numeros.length;
		
	}
}
```
- Podemos usar outra estrutura para o o laço `for`, como no exemplo abaixo:
```java
public class Calculadora {
	static double calcularMedia(int[] numeros) {
		int total = 0;

		for (int numero: numeros) {
			total += numero;
		}

		return (double) total / numeros.length;
		
	}
}
```