___
- Para retornar mais de um valor de um método, precisamos retornar objetos.
- Para isso criamos uma classe contendo apenas as variáveis que queremos retornar. Como no exemplo abaixo:
```java
public class IndiceMassaCorporal {
	double resultado;
	double peso;
	double altura;
}
```
- E agora podemos usar em um método, ou uma variável que vai conter as variáveis dessa classe.
```java
public class Paciente {

	double peso;
	double altura;

	IndiceMassaCorporal calcularIndiceMassaCorporal() {
		IndiceMassaCorporal imc = new IndeceMassaCorporal();
		imc.resultado = peso / (altura * altura);
		imc.peso = peso;
		imc.altura = altura;
	
		return imc;
	}
}
```
- Assim agora para atribuir o valor que retorna desse método a uma variável fazemos da seguinte maneira:
```java
IndiceMassaCorporal imc = paciente.calcularIndiceMassaCorporal();
```
- E obtemos acesso aos valores, partindo da variável de referência.
```java
imc.resultado // retorna o resultado do objeto IndiceMassaCorporal
imc.altura // retorna a altura do objeto IndiceMassaCorporal
imc.peso // retorna o peso do objeto IndiceMassaCorporal
```