___
Para customizar a mensagem de erro, pelo `zod`, é bem simples, passamos como parâmetro a mensagem que queremos no schema. Como no exemplo abaixo:
```ts
const bodySchema = z.object({
	name: z.string({ required_error: "Name is required!"}),
	price: z.number({ required_error: "Price is required!"})
})
```
- Agora quando for lançado uma exceção nesses campos irá aparecer essas mensagens.
