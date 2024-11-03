___
- Como vimos anteriormente, podemos criar [[Criando e invocando um método|métodos]], e esses métodos podem receber parâmetros, e esses parâmetros podem ser utilizados pelo método para realizar algo.
- Como por exemplo, vamos mudar o método `calcular`, para receber dois parâmetros e calcular o `imc`.
```java
IndiceMassaCorporal calcular(double peso, double altura) {
	IndiceMassaCorporal imc = new IndiceMassaCorporal();
	imc.resultado = peso / (altura * altura);
	imc.peso = peso;
	imc.altura = altura;

	return imc;
}
```
- Podemos passar quantos parâmetros forem necessários para o método, mas o ideal é no máximo 3 parâmetros. 