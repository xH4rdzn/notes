___
- Os métodos são comportamentos de uma classe, aqui vamos ver os métodos sem retorno, mas também temos os [[Métodos que retornam|métodos que retornam alguma coisa]].
- Para criar um método que não possui retorno, o declaramos da seguinte maneira:
```java
// Sem parâmetros
void nomeDoMetodo() {
	// Código a ser executado
}

// Com parâmetros
void nomeDoMetodo2(tipoDado nomeVariavel) {
	// Código a ser executado
}
```
- ***Nota-se que usamos a keyword `void` para indicar que esse método não retorna nada***
- Seguindo o nosso exemplo da classe conta, voltamos nela e criamos o método depositar, que não nos retorna nada:
```java
public class Conta {
	int agencia;
	int numero;
	double saldo;
	String titular;

	void depositar(double valor) {
		saldo += valor;
	}
}
```
- Agora que criamos o método na nossa classe Conta, após fazer a instancia desse objeto temos acesso ao método depositar, então fazemos seu seguindo o exemplo:
```java
public class TestaConta {

	public static void main(String args[]) {
		Conta primeiraConta = new Conta(); // Instanciando conta

		primeiraConta.depositar(450.50);
	}
}
```
- Como o nosso método possui um parâmetro a ser recebido, precisamos passar ele entre `()`, como no exemplo acima.
- Mas também podemos ter [[Métodos que retornam|métodos com retorno]]
