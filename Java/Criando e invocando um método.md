___
- Os métodos são comportamentos ou ações de um objeto.
- Os métodos são trechos de código que são referenciados pelo nome, e podem ser chamados por outra parte do nosso programa, a partir de seu nome.
- Para poder criar um método seguimos a seguinte estrutura:
- `tipoDeRetorno nomeDoMétodo(parâmetros)`
- Como no exemplo abaixo:
```java
// tipoDeRetorno nomeDoMétodo
void calcularValorRevenda() {}
```
- *Nota-se que no exemplo acima, o método não possui parâmetros*
- Os métodos só ficam disponíveis, quando tiver uma instância do objeto onde estamos declarando o método.
- Os métodos tem acesso as variáveis de instância da classe na qual ele está. Como no exemplo abaixo:
```java
public class Carro {
	String fabricante;
	String modelo;
	String cor;
	int anoFabricacao;
	Pessoa proprietario;

	void calcularValorRevenda() {
		System.out.printf("Calcular valor de revenda de: %s %d%n", modelo, anoFabricacao);
	}
}
```
- Para chamar o método, precisamos usar a variável que usamos para referenciar ao nosso objeto. Como no exemplo abaixo:
```java
Carro meuCarro = new Carro();
meuCarro.modelo = "Civic";
meuCarro.anoFabricao = 2006;

meuCarro.calcularValorRevenda();
```
