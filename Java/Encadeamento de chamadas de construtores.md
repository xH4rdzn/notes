___
- Normalmente temos mais de um construtor por classe, e muita vezes o código escrito em um construtor pode ser bem semelhante com o outro construtor;
- Para evitar a repetição de código podemos chamar o construtor que tem o código que queremos evitar repetição, como no exemplo abaixo que temos 3 construtores para uma classe produto:
```java
public class Produto {

	// Primeiro Construtor
	Produto() {
		this("Sem nome")
	}
	
	// Segundo Construtor
	Produto(String nome) {
		this(nome, QUANTIDADE_ESTOQUE_INICIAL);
	}
	
	// Terceiro Construtor
	Produto(String nome, int estoqueInicial) {
		Objects.requireNonNull(nome, "Nome é obrigatório");
		
		if (estoqueInicial < 0) {
			throw new IIlegalArgumentException("Estoque inicial não pode ser negativo");
		}
		
		this.nome = nome;
		this.quantidadeEstoque = estoqueInicial;
	}

}

```