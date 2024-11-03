___
- Para criar um método que retorna algo, seguimos a mesma estrutura dos [[Métodos sem retorno|métodos sem retorno]], porém no lugar do `void`, usamos o tipo de dado que queremos que retorne desse método.
- Então seguimos a estrutura:
```java
// retornar dado do tipo boolean
boolean nomeDoMetodo() {}

// retonar dado do tipo int
int nomedoMetodo(){}

// retonar dado do tipo double
double nomeDoMetodo(){}

// retonar dado do tipo String
String nomeDoMetodo(){}
```
- Podemos usar qualquer tipo de dado, inclusive Classes.
- Porém em métodos que retornam algo precisamos usar a keyword `return`, caso contrario, vamos ter um erro de compilação.
- Seguindo os exemplos passados, vamos implementar o método `sacar`, na nossa classe conta:
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
}
```
- Agora para usar esse método, seguimos a mesma estrutura que vimos anteriormente:
```java
public class TestaConta {
	public static void main(String args[]) {
		Conta primeiraConta = new Conta();

		primeiraConta.depoisitar(450.50);
		System.out.println(primeiraConta.saldo); // Imprime 450.50

		boolean conseguiuSacar = primeiraConta.sacar(300);

		if(conseguiuSacar) {
			System.out.println("Saque realizado com sucesso");
		} else {
			System.out.println("Não foi possível realizar o saque");
		}

	}
}
```
- Também temos [[Métodos com referência|métodos que fazem referência]] a outro objeto.