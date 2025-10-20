___
- A operação intermediária ***`limit`*** é utilizada para restringir o número de elementos em uma stream.
- Basicamente, ela cria uma nova stream que contém uma quantidade específica de elementos da stream original.
- A função recebe um número como argumento, que representa o máximo de elementos que serão incluídos na nova stream.
```java
var numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9);

var limitedNumbers = numbers.stream()
	.limit(3)
	.collect(Collectors.toList());
```
- Como no exemplo abaixo:
```java
// 1) Retornar uma lista com os 2 primeiros pedidos que possuem maior valor total  
public static void exercise1() {  
    var orders = Mock.orders();  
  
    var result = orders.stream()  
            .sorted(Comparator.comparing(Order::getPrice).reversed())  
            .limit(2)  
            .collect(Collectors.toList());  
  
    System.out.println(result);
```
- E outro exemplo usando outras operações intermediárias:
```java
// 2) Retornar uma lista com os 3 primeiros clientes que mais possuem itens no pedido  
public static void exercise2() {  
    var orders = Mock.orders();  
  
    var result = orders.stream()  
            .sorted(Comparator.comparing(order -> order.getItems().size(), Comparator.reverseOrder()))  
            .map(order -> order.getClient())  
            .limit(3)  
            .collect(Collectors.toList());  
  
  
    System.out.println(result);
```