___
- Para não instanciarmos um objeto em um estado errado, validamos os argumentos dos construtores, e podemos fazer da seguinte maneira:
```java
public class Produto {

	String nome;
	int quantidadeEstoque

	Produto(String nome, int estoqueInicial) {
		Objects.requireNonNull(nome, "Nome é obrigatório");

		if(estoqueInicial < 0) {
			throw new IllegalArgumentException("Não pode ser negativo");
		}
	}
}
```