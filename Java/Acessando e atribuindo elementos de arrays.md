___
- Para podermos acessar um elemento do array, podemos fazer da seguinte maneira:
```java
public class Principal {
	public static void main(String[] args) {
		int notas[] = {8, 5, 4, 9, 10};

		// Acessando um elemento do array
		System.out.println(notas[0]);
	}
}
```
- Podemos acessar os elementos através de variáveis, como no exemplo abaixo:
```java
public class Principal {
	public static void main(String[] args) {
		int notas[] = {8, 5, 4, 9, 10};

		int posicao = 3;
		System.out.println(notas[posicao]);
	}
}
```
- Podemos fazer cálculos para o índice:
```java
public class Principal {
	public static void main(String[] args) {
		int notas[] = {8, 5, 4, 9, 10};

		int posicao = 3;
		System.out.println(notas[posicao - 1]);
	}
}
```
- Se tentarmos acessar um índice que não existe vai ocorrer uma exceção; `ArrayIndexOutOfBoundsException`;
- E podemos fazer cálculos com os valores do array:
```java
public class Principal {
	public static void main(String[] args) {
		int notas[] = {8, 5, 4, 9, 10};

		int totalNotas = notas[0] + notas[1] + notas[2] + notas[3];
		System.out.println(totalNotas);
	}
}
```
- Se quisermos alterar um valor que já esta no array, fazemos da seguinte maneira:
```java
public class Principal {
	public static void main(String[] args) {
		int notas[] = {8, 5, 4, 9, 10};

		// A primeira posição irá alterar o valor de 8 para 10.
		notas[0] = 10;
	}
}
```