___
- Uma `java.util.List` é uma coleção que pode conter elementos duplicados. Uma `List`, é as vezes chamadas de sequência. Assim como `arrays`, as listas são indexadas a partir do índice zero(isto é, o índice do primeiro elemento é 0).
- Além de ser uma interface que herda definições da `Collection`, uma lista fornece métodos para manipular seus elementos utilizando índices além de, manipular um intervalo especificado de elementos, pesquisar elementos e obter um `ListIterator` para acessar os elementos.
- Conforme estrutura hierárquica da `Collections Framework`, a interface `List` é implementada pelas classes abaixo:

| Nome       | Descrição                                                       |
| ---------- | --------------------------------------------------------------- |
| Vector     | Um array redimensionável com sincronização segura               |
| ArrayList  | Um array redimensionável e indexado mais perfomático            |
| LinkedList | Uma lista encandeada com mais recursos de inserção de elementos |
- Para declarar uma `List`, fazemos como no exemplo abaixo:
```java
import java.util.List;

public class Listas {
	public static void main(String[] args) {
		List linguagens = new ArrayList();
	}
}
```
- Para adicionar elementos em uma lista, usamos o método `add`:
```java
import java.util.List;

public class Listas {
	public static void main(String[] args) {
		List linguagens = new ArrayList();

		linguagens.add("java");
	}
}
```
- Para ver o comprimento da lista, usamos o método `size`:
```java
import java.util.List;

public class Listas {
	public static void main(String[] args) {
		List linguagens = new ArrayList();

		linguagens.add("java");
		System.out.println(linguagens.size()); // Retorna 1.
	}
}
```
- Para recuperar um elemento de algum índice, usamos o método `get`:
```java
import java.util.List;

public class Listas {
	public static void main(String[] args) {
		List linguagens = new ArrayList();

		linguagens.add("java");
		linguagens.add("php");
		linguagens.add("go");
		linguagens.add("javascript");
		System.out.println(linguagens.size()); // Retorna 4.

		System.out.println(linguagens.get(2)); // Retorna "go";
	}
}
```
- Para remover um elemento usamos o método `remove`:
```java
import java.util.List;

public class Listas {
	public static void main(String[] args) {
		List linguagens = new ArrayList();

		linguagens.add("java");
		linguagens.add("php");
		linguagens.add("go");
		linguagens.add("javascript");

		// Podemos remover pelo objeto;
		linguagens.remove("go");
	}
}
```

