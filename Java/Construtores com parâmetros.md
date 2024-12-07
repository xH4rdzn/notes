___
- Os [[Criando e chamando construtores|construtores]], podem receber argumentos (parâmetros), assim como fazemos com os métodos;
- Quando queremos que para fazer a instância de um certo objeto seja passado esses argumentos, fazemos como no exemplo abaixo:
```java
public class Produto {
	String nome;
	int quantidadeEstoque;

	Produto(String nome, int quantidadeEstoque) {
		this.nome = nome;
		this.quantidadeEstoque = quantidadeEstoque;
	}
}
```
*Quando temos um construtor com parâmetros, ele se torna obrigatório a ser passado, no momento da instância do objeto.*
- Então para fazer uma instância do exemplo acima, teríamos que fazer da seguinte maneira:
```java
public class Principal {
	public static void main(String[] args) {
		Produto produto1 = new Produto("Camisa", 10);
	}
}
```
