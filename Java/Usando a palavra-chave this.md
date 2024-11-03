___
- A keyword `this`, se referência ao próprio objeto.
- Por exemplo, vamos criar um método que altera o valor de custo de um produto
```java
public class Produto {
	double precoCusto;
	double precoVenda;

	void alterarPrecoCusto(double precoCusto) {
		precoCusto = precoCusto;
	}
}
```
- O método acima, não irá alterar nada na variável de instância da classe produto
- Uma maneira de solucionar o problema é alterar o nome da variável que é recebida como parâmetro.
```java
public class Produto {
	double precoCusto;
	double precoVenda;

	void alterarPrecoCusto(double novoPrecoCusto) {
		precoCusto = novoPrecoCusto;
	}
}
```
- Outra maneira de resolver esse problema é usando a keyword `this`, que faz referência ao objeto em si, deixando o nosso método da seguinte maneira:
```java
public class Produto {
	double precoCusto;
	double precoVenda;

	void alterarPrecoCusto(double precoCusto) {
		this.precoCusto = precoCusto;
	}
}
```
- Na maneira acima, não precisamos alterar o nome da variável, pois a palavra `this`, já faz a referência a variável de instância do objeto.