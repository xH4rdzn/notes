___
- Toda classe java que criamos, elas possuem construtores e quando instanciamos um objeto dessa classe, na verdade estamos invocando o construtor,m para podermos instanciar o objeto.
```java
public class Principal {
	public static void main(String[] args) {
		Produto produto1 = new Produto();
	}
}
```
- A keyword `new`, na verdade está invocando um construtor da classe, no exemplo acima por exemplo da classe *produto*;
- Toda classe em java, tem pelo menos um construtor;
- Quando não declaramos um construtor de forma explicita, o compilador faz isso de maneira automaticamente, gerando um construtor sem parâmetros, também conhecido como **construtor padrão**(`construtor default`).
- Para criarmos um construtor de uma classe seguimos o exemplo abaixo:
```java
public class Produto {

	Produto() {
		// Código...
	}

}
```
**Nota-se, que o construtor possui o mesmo nome da classe, e não tem nenhum tipo de retorno.*
- O construtor é chamado quando instanciamos a classe.