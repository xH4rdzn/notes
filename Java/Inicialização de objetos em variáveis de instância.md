___
- Quando temos uma [[Composição de objetos|composição]] entre objetos, podemos inicializar ele a partir de um atributo de classe.
- Como visto anteriormente essas variáveis possuem um valor [[Valores padrão e inicialização de variáveis de instância|padrão]] ao ser inicializadas. E como é uma classe recebe o valor de `null`.
- Mas podemos inicializar ela da seguinte maneira:
```java
public class Carro {
	String fabricante;
	String modelo;
	String cor;
	int anoLancamento;
	Pessoa proprietario = new Pessoa();
}
```
- Logo ao instanciarmos a *classe carro*, vamos inicializar também um objeto do tipo *pessoa*. Como demonstrado no exemplo acima.
- Na classe `pessoa`, também podemos inicializar os `atributos`.
```java
public class Pessoa {
	String nome = "João";
	String cpf;
	int anoNascimento;
}
```
- Mesmo podendo fazer isso, não é *correto*.