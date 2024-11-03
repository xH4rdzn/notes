___
- Para as classes que criamos para poder retornar um objeto, podemos torna-lá, mais rica, adicionando comportamentos, que podemos usar em mais de um lugar, assim evitando duplicidade de código.
- E caso precise fazer uma alteração futura, fica mais fácil e prático de alterar em todo o programa de uma vez.
- No exemplo abaixo, voltamos a classe `IndiceMassaCorporal`, e adicionamos um método para dizer se de acordo com o `resultado`, um paciente está com obesidade.
```java
public class IndiceMassaCorporal {

	double resultado;
	double altura;
	double peso;

	boolean estaComObesidade() {
		return resultado >= 30;
	}
}
```
- E o usamos, igual usamos métodos, a partir de uma variável de referência.