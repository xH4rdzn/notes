___
- Para evitar duplicidade de código, podemos usar os métodos para fazer coisas muitos simples, como vimos [[Métodos com Retorno|anteriormente]], o código que fazemos o calculo do tempo de uso, pode acabar se repetindo em outros lugares, por isso podemos separar ele em um método.
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
- E trocamos a variável: `tempoDeUsoEmAnos`, por esse método que vamos criar abaixo:
```java
int calcularTempoDeUsoEmAnos() {
	return 2024 - anoFabricacao;
}
```
- E para usarmos esse método dentro do próprio objeto, na classe, podemos usar o método de maneira direta. Como no exemplo abaixo:
```java
public class Carro {
	String fabricante;
	String modelo;
	String cor;
	int anoFabricacao;
	double precoCompra;
	Pessoa proprietario;

	int calcularTempoDeUsoEmAnos() {
		return 2024 - anoFabricacao;
	}

	double calcularValorRevenda() {
		// Chamando o método calcularTempoDeUsoEmAnos
		int tempoDeUsoEmAnos = calcularTempoDeUsoEmAnos();
		int vidaUtilEmAnos = 20;

		double valorRevenda = (precoCompra / vidaUtilEmAnos) * (vidaUtilEmAnos - tempoDeUsoEmAnos);

		if (valorRevenda < 0) {
			valorRevenda = 0;
		}

		return valorRevenda;
	
	}
}
```