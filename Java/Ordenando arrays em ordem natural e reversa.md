___
- Para podermos ordenar um array, podemos usar a classe utilitária `sort`, para organizar o nosso array;
```java
import java.util.Arrays;

public class Principal {
	public static void main(String[] args) {
		int[] notas = {8, 5, 4, 10, 9};

		Arrays.sort(notas);
	}
}
```
- Mas as vezes queremos na ordem *decrescente*, para fazer isso podemos usar da seguinte maneira:
```java
import java.util.Arrays;

public class Principal {
	public static void main(String[] args) {
		int[] notas = {8, 5, 4, 10, 9};

		Arrays.sort(notas, Comparator.reverseOrder());
	}
}
```
- Mas dessa maneira só podemos usar apenas os tipos `Wrappers`;
- Caso contrário irá dar um erro de compilação;