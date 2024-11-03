___
- As vezes temos [[Métodos com argumentos|métodos]] que recebem múltiplos parâmetros, e esses parâmetros representam algo do mundo real.
- Então criamos uma classe para representar esse objeto que vão possuir as variáveis que vamos utilizar nesse método.
- Como por exemplo o método de `calcular`, da nossa calculadora de IMC, ela pode receber um objeto do tipo `Paciente`.
- Então, para passarmos um objeto do tipo `Paciente`, para o método `calcular`, fazemos da seguinte maneira:
```java
IndiceMassaCorporal calcular(Paciente paciente) {
	IndiceMassaCorporal imc = new IndiceMassaCorporal();
	imc.resultado = paciente.peso / (paciente.altura * paciente.altura);
	imc.peso = paciente.peso;
	imc.altura = paciente.altura;

	return imc;
}
```
- *Nota-se que usamos como referência o **paciente** que é nome da variável que damos no método*.
- E agora ao usar o método, precisamos de um objeto do tipo `Paciente`, e passamos ele para o método `calcular`. Como no exemplo a baixo:
```java
Paciente igor = new Paciente();
igor.peso = 85;
igor.altura = 1.73;

IndiceMassaCorporal imc = calculadoraImc.calcular(igor);
```
- E agora podemos usar os dados do objeto `igor`, para o método `calcular`; 