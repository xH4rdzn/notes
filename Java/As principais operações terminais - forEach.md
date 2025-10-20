___
- A operação terminal ***`forEach`*** é utilizada para iterar sobre cada elemento de uma stream e realizar alguma lógica especifica.
- Essa operação aceita um ***Consumer*** como argumento, que é uma função que aceita um único argumento e não retorna nenhum resultado.
- É comum utilizar essa operação para os seguintes casos:
	- Aplicar alguma lógica de negócio:
```java
clients.stream()
	.filter(client -> client.getBirthDate().getMonth().equals(today.getMonth()))
	.forEach(client -> {
		// Enviar e-mail promocional
	});
```
- Modificar um estado externo
```java
orders.stream()
	.filter(order -> order.getClient().getBirthDate().getMonth().equals(today.getMonth()))
	.forEach(order -> {
		order.applyDiscount(10);
		
		discountedOrders.add(order);
	})
```