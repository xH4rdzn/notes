___
- Esses métodos podem alterar o valor do objeto que é recebido como parâmetro. Como no exemplo a seguir que temos a classe `Produto`, e a classe `ServicoDePrecificacao`, que é responsável por `definir o preço da venda`.
```java
public class Produto {

	double precoCusto;
	double precoVenda;
}

public class ServicoPrecificacao {

	void definirPrecoVenda(Produto produto, double percentualMargemLucro) {
		produto.precoVenda = produto.precoCusto * ((percentualMargemLucro / 100) + 1);
	}
}
```
- E agora usamos da seguinte maneira:
```java
public class Principal {
	public static void main(String[] args) {

		Produto novoProduto = new Produto();
		novoProduto.precoCusto = 100;

		ServicoPrecificacao servicoDePrecificacao = new ServicoPrecificacao();

		servicoDePrecificacao.definirPrecoVenda(produto, 20);
		// O método acima deve retornar 120.

	}
}
```
- Ele altera a variável `precoVenda`, que está dentro da classe `Produto`.