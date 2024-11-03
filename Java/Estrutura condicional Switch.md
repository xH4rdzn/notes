___
- Usamos essa estrutura condicional, quando temos que tomar uma decisão, baseada apenas em uma variável
-  Usamos o `switch`, da seguinte maneira:
```java
switch (variavel) {
	case valor:
		// Código caso for esse valor;
	case outroValor:
		// Código caso for esse outroValor;
	default:
		// Código a ser executado, se não for nenhum caso;
}
``` 
- No exemplo acima, se for satisfeito a condição do `case valor`, todos os `case`, abaixo dele serão executados inclusive o `default`.
- Para evitar esse comportamento usamos o `break`, para executar apenas o `case` satisfeito. Alterando o nosso código para o seguinte exemplo:
```java
switch (variavel) {
	case valor:
		// Código caso for esse valor;
		break;
	case outroValor:
		// Código caso for esse outroValor;
		break;
	default:
		// Código, caso não for nehum caso;
		break;
}
```
- A partir do `Java 14`, podemos usar o `switch` de uma nova maneira, nesta nova maneira não precisamos usar o `break`, e podemos passar varias opções para um `case`, como no exemplo a seguir:
```java
String diaSemana;
String horarioFuncionamento;
switch (diaSemana) {
	case "seg" -> horarioFuncionamento = "Fechado";
	case "ter", "qua", "qui", "sex" -> horarioFuncionamento = "08:00 às 18:00";
	case "sab", "dom" -> horarioFuncionamento = "08:00 às 12:00";
	default -> horarioFuncionamento = "Dia inválido";
}
```
- Podemos também usar o que chamamos de `switch expressions`, que é usado para atribuir o valor de uma variável, a partir do `switch`, como no exemplo a seguir:
```java
String horarioFuncionamento = switch (diaSemana) {
	case "seg" -> "Fechado";
	case "ter", "qua", "qui", "sex" -> "08:00 às 18:00";
	case "sab", "dom" -> "08:00 às 12:00";
	default -> "Dia Inválido";
}
```
- No `switch expressions`, se os casos forem infinitos, temos que usar o `default`.
- Podemos também criar um bloco, caso tenhamos que aplicar uma lógica especifica.
- E usamos a keyword `yield`, para produzir um valor. Como no exemplo a seguir:
```java
case "seg" -> {
	if (mes == 12) {
		yield "08:00 às 16:00";
	}
	yield "Fechado";
}
```