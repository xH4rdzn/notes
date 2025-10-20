___
- A operação terminal ***`reduce`*** é utilizada para combinar os elementos de uma stream em um único valor.
- Isso é feito aplicando repetidamente uma função aos elementos da stream até que um único valor seja produzido.
- Essa operação pode ser usada das seguintes formas:
	- Sem valor inicial
```java
var numbers = Arrays.asList(1, 2, 3, 4, 5);

var result = numbers.stream().reduce((n1, n2) -> n1 * n2);
```
 - Esta forma retorna um ***`Optional`***, pois a stream pode estar vazia.
	- Com valor inicial
```java
var numbers = Arrays.asList(1, 2, 3, 4, 5);

var result = numbers.stream().reduce(1000, Integer::sum);
```
- Nesta forma, o valor inicial é utilizado como ponto de partida para a acumulação.