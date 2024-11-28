___
- Vamos utilizar o `Zod`, para validar os dados
- Utilizamos o comando abaixo para instalar o `Zod`
```zsh
npm i zod
```
- E agora dentro do nosso [[Middeware De Tratamento de Exceções|middleware]] para tratar erros, vamos importar o `ZodError`
```ts
import { ZodError } from "zod"
```
- E agora dentro do nosso [[Middeware De Tratamento de Exceções|middleware]], podemos verificar se é um error do tipo `ZodError`, adicionando a seguinte verificação em nosso *middleware*
```ts
if(error instanceof ZodError) {
	return response.status(400).json({
		message: "validation error",
		issues: error.format(),
	})
}
```