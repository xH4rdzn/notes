___
- Para variáveis de instância (propriedades), com o modificador `final`, temos que atribuir o seu valor diretamente a variável, ou podemos atribuir ela por meio de um construtor.
- Como no exemplo abaixo que vamos adicionar a propriedade *código* na classe **Produto**
```java
public class Produto {
	
	final String codigo;
	String nome;
	int quantidadeEstoque;
	
	Produto(String nome, int estoqueInicial) {
		this.nome = nome;
		this.quantidadeEstoque = estoqueInicial;
		this.codigo = UUID.randomUUID().toString();
	}
}
```
- Desta maneira toda vez que formos instanciar um nome objeto do tipo Produto, vai ser gerado um novo *código* e essa variável de instância se torna **imutável**;