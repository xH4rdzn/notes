___
- Agora que [[Instalando o Zod|instalamos o zod]], vamos utilizar ele para poder fazer nossas validações de maneira mais `clean`. Como no exemplo abaixo que vamos validar a requisição de criar um produto:
1. Primeiro importamos o `zod`
```ts
import { z } from "zod"
```
2. Agora na rota que queremos validar, no caso a rota de criar um produto vamos fazer a seguinte maneira:
```ts
const bodySchema = z.object({
	name: z.string(),
	price: z.number()
})
```
3. Agora para passar o nosso `schema` para a nossa `request.body`, fazemos da seguinte maneira
```ts
// Destruturando o objeto
const { name, price } = bodySchema.parse(request.body)

// Referenciando o objeto
const body = bodySchema.parse(request.body)
body.name
body.price
```