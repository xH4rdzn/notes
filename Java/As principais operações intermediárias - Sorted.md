___
- A operação intermediária ***`sorted`*** é utilizada para ordenar elementos de uma stream.
- Esta operação é útil quando desejamos garantir que os elementos estejam em uma ordem específica antes de realizar operações subsequentes, como mapeamento, filtragem ou coleta.
```java
var names = Arrays.asList("Pedro", "Ana", "Marcos", "Vanessa");

var sortedNames = names.stream()
	.sorted()
	.collect(Collectors.toList());
```
- Essa operação também pode receber um ***`Comparator`*** como argumento, que permite uma ordenação customizada dos elementos de uma stream.
```java
var names = Arrays.asList("Pedro", "Ana", "Marcos", "Vanessa");

var sortedNames = names.stream()
	.sorted(Comparator.comparing(String::length))
	.collect(Collectors.toList());
```