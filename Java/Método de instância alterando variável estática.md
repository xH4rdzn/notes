___
- Podemos criar métodos para alterar variáveis estáticas
```java
public class Produto {

	static double custoEmbalagem;

	double precoCusto;
	double precoVenda;

	void alterarCustoEmbalagem(double custoEmbalagem) {
		// Fazemos referência a variável static da seguinte maneira:
		Produto.custoEmbalagem = custoEmbalagem;
	}

}
```
-  Nota-se que para acessarmos a variável `custoEmbalagem`, usamos a classe e não a keyword `this`.
- ***Devemos ter cuidado com métodos de instância que fazem alterações em variáveis estáticas, pois podem acabar confundindo, como se ela fizesse referência a um objeto instanciado.***
