___
- A operação terminal ***`max`*** é utilizada para encontrar o maior elemento de uma stream de acordo com um comparador fornecido.
- Essa operação espera receber um ***Comparator*** como argumento, que define a ordem dos elementos para determinar para determinar o maior.
- Além disso, ela retorna um ***Optional***, pois a stream pode estar vazia, e neste caso, não há um valor máximo para ser retornado.
```java
var names = Arrays.asList("Pedro", "Ana", "Marcos", "Vanessa");

var biggestName = names.stream()
	.max(Comparator.comparing(String::length));
	
	biggestName.ifPresent(System.out::println);
```
