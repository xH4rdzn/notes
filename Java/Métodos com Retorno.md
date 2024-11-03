___
- Como vimos [[Criando e invocando um método|anteriormente]], ao criar um método precisamos definir o tipo de Retorno, que esse método vai retornar.
	- `void` -> Significa que o método não vai retornar nada.
	- `double` -> Significa que o método vai retornar um valor do tipo `double`.
- Todo método que tem que retornar algo, precisa de um `return`;
- E para retornar usamos a keyword `return`. Então alterando o código visto [[Criando e invocando um método|anteriormente]]:
```java
double calcularValorRevenda() {
	int tempoDeUsoEmAnos = 2024 - anoFabricacao;
	int vidaUtilEmAnos = 20;

	double valorRevenda = (precoCompra / vidaUtilEmAnos) * (vidaUtilEmAnos - tempoDeUsoEmAnos);

	if (valorRevenda < 0) {
		valorRevenda = 0;
	}

	return valorRevenda;
}
```
- Todo código abaixo do `return`, não é executado, em outras palavras ele para a execução do método.
