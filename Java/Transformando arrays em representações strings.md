___
- Quando trabalhamos com `arrays`, as vezes surge a necessidade de transformar esse `array` em uma `String`, para poder por exemplo fazer um debug;
- Para transformar um `array` em `String`, fazemos da seguinte maneira:
```java
import java.util;Arrays;

public class Calculadora {
	public static void main(String[] args) {
		int[] notas = {8, 5, 4, 9, 10};

		String notasEmString = Arrays.toString(notas);

		System.out.println(notasEmString);
	}
}
```