___
- Para validarmos os dados do usuário, vamos utilizar o [[Adicionando Zod|zod]], então em nosso `controller`fazemos a sua importação:
```ts
import { z } from "zod"
```
- E no nosso método `create`, vamos adicionar o seguinte trecho:
```ts
const bodySchema = z.object({
	name: z.string().trim().min(1),
	email: z.string().email(),
	password: z.string().min(6),
})
```
- Agora podemos fazer a desestruturação desses itens da seguinte maneira:
```ts
const { name, email, password } = bodySchema.parse(request.body)
```
*Essas informações precisam ser passadas no `Corpo da requisição`, então no Insomnia, adicionamos um `JSON`, com essas informações*
```json
{
	"name": "Igor Coelho",
	"email": "igor@email.com",
	"password": "123456"
}
```
- Se passarmos os dados de maneira correta ele não irá dar erro de validação;