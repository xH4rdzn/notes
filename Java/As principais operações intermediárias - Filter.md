___
- A operação intermediária ***filter*** é utilizada para selecionar elementos de uma stream que satisfazem um determinado predicado. O predicado é uma função que recebe um argumento e retorna um resultado booleano. Apenas os elementos para os quais o predicado retornar verdadeiro que serão mantidos na stream resultante.
```java
var names = Arrays.asList("Pedro", "Ana", "Marcos", "Vanessa");

var filteredNames = names.stream()
	.filter(name -> name.length() => 6)
	.collect(Collectors.toList());
	
System.out.println(filtredNames);	
```