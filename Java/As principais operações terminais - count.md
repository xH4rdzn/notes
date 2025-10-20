___
- A operação terminal ***`count`*** é utilizada para contar a quantidade de elementos em uma stream.
- É uma operação bem simples, mas extremamente útil para determinar o tamanho de um conjunto de dados após aplicar operações intermediárias, como filtragem, mapeamento ou outras transformações.
```java
var numbers = Arrays.asList(1, 8, 6, 4, 9, 3, 7, 2, 5);

var totalElements = numbers.stream()
	.map(number -> number * 3)
	.filter(number -> number > 20)
	.count();
```