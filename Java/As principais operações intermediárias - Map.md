___
- A operação intermediária ***`map`*** é utilizada para transformar os elementos de uma stream.
- Ela recebe uma função como argumento e essa função é aplicada a cada elemento da stream, retornando um novo elemento, que pode ser de um tipo diferente do original.
- O resultado é uma nova stream composta pelos elementos transformados
```java
var names = Arrays.asList("Pedro", "Ana", "Marcos", "Vanessa");

var upperCaseNames = names.stream()
	.map(String::toUpperCase)
	.collect(Collectors.toList());
	
System.out.println(upperCaseNames);	
```
- Um exemplo mudando o tipo de dado com ***`map`***
```java
var names = Arrays.asList("Pedro", "Ana", "Marcos", "Vanessa");

var lengthNames = names.stream()
	.map(String::length)
	.collect(Collectors.toList());
	
System.out.println(upperCaseNames);	
```
- Podemos aplicar outras operações intermediárias como o ***[[As principais operações intermediárias - Filter|Filter]]***, antes de usar o ***`map`***