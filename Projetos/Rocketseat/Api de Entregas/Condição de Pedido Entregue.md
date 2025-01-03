___
- Quando um pedido for entregue, ele não deve mais receber logs, então precisamos criar uma condicional para isso;
- Voltamos ao `deliveryLogsController`e alteramos no método `create`, adicionando a nova verificação abaixo:
```ts
if(delivery.status === "delivered") {
	throw new AppError("This order has already been delivered")
}
```
