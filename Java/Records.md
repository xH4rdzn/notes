___
- É um tipo especial de classe, que é imutável;
- Para declarar um `record`, fazemos da seguinte maneira:
```java
public record Horario(int hora, int minuto) {}
```
- O que passamos entre `()`, se tornam as nossas variáveis de instância, que já são inicializadas como `final`;
- Ele cria um construtor com os argumentos passado no `()`;
- Se quisermos fazer uma validação no construtor podemos fazer como no exemplo abaixo:
```java
public record Horario(int hora, int minuto) {

	public Horario(int hora, int minuto) {
		if (hora < 0 || hora > 23) {
			throw new IllegalArgumentExcepetion("");
		}
		
		if (minuto < 0 || minuto > 59) {
			throw new IllegalArgumentExcepetion("");
		}
	}

}
```
- Outra maneira também é fazendo da seguinte maneira:
```java
public Horario {
	// Lógica ou validação dos argumentos passados.
}
```
- A maneira acima implementamos principalmente quando queremos validar os parâmetros passados;
- ***Podemos criar métodos, só não podemos alterar os valores das variáveis de instância***;
- Para instanciar é semelhante a uma classe;