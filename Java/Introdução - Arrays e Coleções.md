___
- Arrays ou coleções são estruturas de dados que consistem em itens ou elementos relacionados a um mesmo tipo ou `sub-tipo` de dados;

#### Arrays
- Consideramos também um array, como um grupo de posições reservadas na memória para armazenar elementos localizados através de um índice que se inicia com zero;
- Abaixo vamos criar um array
```java
public class Arrays {
	public static void main(String[] args) {
		Integer[] array = new Integer[6];

		array[0] = 2;
		array[1] = 4;
		array[2] = 10;
		array[3] = 5;
		array[4] = 15;
		array[5] = 3;
	}
}
```
- Nota-se que para fazer a declaração do array precisamos definir seu tipo com o `[]`, no caso usamos o tipo de dado `Integer`;
- Mas poderíamos usar qualquer outro tipo de dado;
- O atributo `length`, retorna o tamanho do array;
```java
public class Arrays {
	public static void main(String[] args) {
		Integer[] array = new Integer[6];

		array[0] = 2;
		array[1] = 4;
		array[2] = 10;
		array[3] = 5;
		array[4] = 15;
		array[5] = 3;

		System.out.println(array.length);
	}
}
```