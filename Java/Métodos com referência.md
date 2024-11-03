___
- Também temos métodos que fazem referência a outros objetos.
- Para declarar um método que faz referência a outro objeto, fazemos da seguinte forma:
```java
tipoDeRetorno nomeDoMetodo(tipoDeDado nomeVariavel, tipoClasse nomeVariavel) {}
```
- ***Nota-se que o segundo parâmetro do método acima é um tipoClasse, em outras palavras é o nome da classe que esse método vai receber como parâmetro**.
- Seguindo os exemplos passados, vamos implementar o método `transferir`, em nossa classe `Conta`:
```java
public class Conta {
	int agencia;
	int numero;
	String titular;
	double saldo;

	// método sem retorno
	void depositar(double valor) {
		saldo += valor;
	}

	// Método com retorno
	boolean sacar(double valor) {
		if(saldo >= valor) {
			saldo -= valor;
			return true;
		} else {
			return false;
		}
	}

	// Método que faz referência
	void transferir(double valor, Conta destino) {
		
	}
}
```
- Como vamos transferir de uma conta para outra, já temos um `objeto principal`, então para poder fazer referência a esse `objeto principal`, usamos a keyword `this`, que faz referência ao objeto que estamos usando, no caso o objeto principal. Então nosso método vai ficar da seguinte maneira:
```java
public class Conta {
	int agencia;
	int numero;
	String titular;
	double saldo;

	// método sem retorno
	void depositar(double valor) {
		saldo += valor;
	}

	// Método com retorno
	boolean sacar(double valor) {
		if(saldo >= valor) {
			saldo -= valor;
			return true;
		} else {
			return false;
		}
	}

	// Método que faz referência
	void transferir(double valor, Conta destino) {
		boolean conseguiuSacar = this.sacar(valor);
		if(conseguiuSacar) {
			destino.depositar(valor);
		}
	}
}
```