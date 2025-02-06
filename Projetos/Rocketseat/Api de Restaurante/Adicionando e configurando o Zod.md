___
- Vamos utilizar o `zod`, para fazer a validação de dados que chegam na nossa requisição.
- Para isso vamos instalar ele usando o comando:
```zsh
npm i zod
```
- Agora vamos no arquivo `errorHandling`, e vamos adicionar a verificação do `zod`, então acrescentamos:
```ts
import { ZodError } from "zod"

if(error instanceof ZodError) {
	return response
	.status(400)
	.json({ message: "validation error", issues: error.format()})
}
```