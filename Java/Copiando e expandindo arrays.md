___
- Podemos copiar os arrays, e fazemos como no exemplo abaixo:
```java
public class Principal {
	public static void main(String[] args) {
		int[] numerosJogo1 = {25, 11, 8, 46, 37, 14};


		int[] numerosJogo2 = Arrays.copyOf(numerosJogo1, numerosJogo1.length)
	}
}
```
*Como primeiro parâmetro passamos o array que queremos copiar, e o segundo parâmetro é a quantidade de posições que queremos copiar, podendo ser um número literal ou que nem está no exemplo o total do array que está sendo copiado*;
- Podemos usar o método `copyOf`, para expandir o tamanho do array, como demostrado no exemplo abaixo:
```java
public class Principal {
	public static void main(String[] args) {
		int[] numerosJogo1 = {25, 11, 8, 46, 37, 14};


		int[] numerosJogo2 = Arrays.copyOf(numerosJogo1, numerosJogo1.length + 1)
	}
}
```
*A cópia criada, vai ter uma posição a mais do que o array original*
- 