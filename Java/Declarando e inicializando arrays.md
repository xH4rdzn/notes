___
- Quando precisamos armazenar uma lista de valores podemos usar um `array`;
- Os `arrays` são conhecido também como vetores, é um tipo de objeto de armazenar um número fixo de valores de um mesmo tipo, mas nós que definimos a quantidade de itens que queremos armazenar;
- Para declarar um array seguimos o exemplo abaixo:
```java
// Declaração de arrays
public class Principal {
	public static void main(String[] args) {
		int[] notas;
	}
}
```
- Nota-se que depois do tipo de dado que o array vai armazenar passamos os `[]`. outra maneira também é passando da seguinte maneira:
```java
// Declaração de arrays
public class Principal {
	public static void main(String[] args) {
		int notas[];
	}
}
```
- Mas o recomendado é declarar como no primeiro exemplo;
- Mas até agora só declaramos a variável, agora precisamos instanciar o objeto do tipo `array`, para fazermos isso seguimos o exemplo abaixo:
```java
public class Principal {
	public static void main(String[] args) {
		int notas[] = new int[10];
	}
}
```
- *Passamos entre os `[]`, a quantidade de valores que vão poder ser armazenados nesse array*;
- As posições de um array em Java, começa sempre do 0, podemos chamar essas posições de `índice`;
- Quando formos acessar os elementos do array, vamos utilizar os `índices`;
- Se quisermos iniciar o array com valores específicos, podemos fazer da seguinte maneira:
```java
public class Principal {
	public static void main(String[] args) {
		int notas[] = new int[]{8, 5, 4, 9, 10};
	}
}
```
- Outra maneira de inicializar o array:
```java
public class Principal {
	public static void main(String[] args) {
		int notas[] = {8, 5, 4, 9, 10};
	}
}
```
 