___
- A operação terminal ***`min`*** é utilizada para encontrar o menor elemento de uma stream de acordo com um comparador fornecido.
- Essa operação espera receber um ***Comparator*** como argumento, que define a ordem dos elementos para determinar o menor.
- Além disso, ela retorna um ***Optional***, pois a stream pode estar vazia, e neste caso, não há um valor mínimo para ser retornado.
```java
var numbers = Arrays.asList(9, 3, 6, 2, 8, 3, 7, 8, 1);

var minNumbers = numbers.stream()
	.min(Integer::compareTo);
	
System.out.println(minNumber); // Optional[1]
minNumber.ifPresent(System.out::println); // 1 
```