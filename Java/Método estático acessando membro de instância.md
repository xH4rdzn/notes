___
- Em métodos estáticos, não podemos acessar variáveis de instância.
- Então, para podermos usar as variáveis de uma instância de um objeto, passamos a instância que queremos como parâmetro de um método estático.
```java
static double imprimirTotalDeCustos(Produto produto) {

	return produto.precoCusto + Produto.custoEmbalagem;

}
```
- *Nota-se que produto é diferente de Produto*, um se referência a classe e a outra a variável que é passada como parâmetro para o método.