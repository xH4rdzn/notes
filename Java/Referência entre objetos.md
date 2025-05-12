___
- Quando usamos a keyword `new`, é alocado um novo espaço na memoria, então cada objeto instanciando, vai para um novo espaço em memoria.
```java
public class Example {
	String title;
}


public static void main() {
	Example minhaClasse = new Example();
}
```
- Caso tenhamos dois objetos apontando para um mesmo espaço em memoria, quando alterarmos um atributo em uma variável, a outra automaticamente vai mudar também.
```java
public static void main() {
	Example minhaClasse = new Example();
	Example minhaOutraClasse = minhaClasse;
}
```
- Podemos usar essas referências também para poder fazer [[Composição entre objetos]]. Que vamos ver um pouco mais pra frente.