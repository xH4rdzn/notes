___
- Quando queremos ter diversas maneiras de instanciar um objeto, podemos fazer uma sobrecarga dos construtores.
- Para fazermos isso podemos fazer como no exemplo abaixo:
```java
public class Produto {
	String nome;
	int quantidadeEstoque;

	Produto(String nome, int estoqueInicial) {
		this.nome = nome;
		this.quantidadeEstoque = estoqueInicial;
	}

	Produto(String nome) {
		this.nome = nome;
	}
}
```
- E para chamar esse construtor, basta passarmos apenas o parâmetro no qual definimos
```java
public class Principal {
	public static void main(String[] args) {
		Produto produto1 = new Produto("Picanha", 50);
		Produto produto2 = new Produto("Fraldinha");
	}
}
```
- Se quisermos ter um construtor sem argumentos, o criamos da seguinte maneira:
```java
public class Produto {

	String nome;
	int quantidadeEstoque;

	Produto() {
	
	}

	Produto(String nome) {
		this.nome = nome;
	}

	Produto(String nome, int estoqueInicial) {
		this.nome = nome;
		this.quantidadeEstoque = estoqueInicial;
	}
	
}
```
**Lembrando que todos os parâmetros que passamos para o construtor, se tornam obrigatório;**
