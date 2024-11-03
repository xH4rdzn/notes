___
- Para criar uma classe, usamos a keyword, `class`, e um modificador de acesso para deixar essa classe visível para toda a nossa aplicação, utilizamos a keyword `public`, então criamos a nossa classe da seguinte maneira:
```java
public class nomeDaClasse {}
```
- Assim já vamos criar a nossa classe.
- Agora separamos a nossa classe entre atributos e métodos;
- Os atributos são variáveis, que mudam de acordo com cada objeto, em outras palavras são características daquele objeto em especifico.
```java
public class Conta {

	String titular;
	int agencia;
	int numero;
	double saldo;
}
```
``No exemplo acima, estamos declarando atributos de que uma Conta pode ter
- Lembrando que a classe, é apenas um modelo, ela não é uma conta em si, mas um modelo que vai ser usado para criar um objeto do tipo conta.
- Vamos falar sobre métodos na nota: [[Métodos sem retorno]], [[Métodos que retornam]] e [[Métodos com referência]];