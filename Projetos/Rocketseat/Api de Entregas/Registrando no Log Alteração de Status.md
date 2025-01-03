___
- Podemos criar um novo *Log*, a cada atualização do status do pedido, para fazer isso voltamos ao `deliveryStatusController`, e antes de retornar a reposta, adicionamos o seguinte código:
```ts
await prisma.deliveryLog.create({
	data: {
		deliveryId: id,
		description: status,
	}
})
```
- Desta maneira, ao mudar o status de uma entrega, ele gera um `Log`;
