___
- Quando temos diversos objetos instanciados a partir de uma mesma classe, todos eles possuem as mesmas variáveis de instância, mas possuem valores diferentes, mas as vezes precisamos de atributos que compartilham entre todos os objetos daquela classe.
- Então para fazer uma variável que vai ser global a todos os objetos daquela mesma classe, usamos a keyword `static`, que é um modificador.
```java
public class Produto {
	static double custoEmbalagem;
	double precoCusto;
	doublePrecoVenda;
}
```
- Agora todos os objetos da classe `Produto`, tem acesso a variável de instância `custoEmbalagem`, porém essa variável é igual para todas as instâncias desse objeto.
- Em outras palavras, se mudarmos em um objeto, vai alterar em todos os outros objetos da mesma classe. Como no exemplo a seguir:
```java
public class Principal {
	public static void main(String[] args) {
		Produto produto1 = new Produto();
		Produto produto2 = new Produto();

		// Não é recomendado acessar essa variável diretamente
		produto1.custoEmbalagem = 10;
		produto2.custoEmbalagem = 15;

		// retorno no console é 15, pois foi a ultima alteração a variável custoEmbalagem.
	}
}
```
- A maneira mais correta de acessar essa variável é fazendo da seguinte maneira:
```java
public class Principal {
	public static void main(String[] args) {
		Produto produto1 = new Produto();
		Produto produto2 = new Produto();

		Produto.custoEmbalagem = 15;
	}
}
```
- No exemplo acima, acessamos diretamente a variável pela classe, e não pela instância do objeto.