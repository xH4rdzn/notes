___
- Agora vamos instalar a seguinte biblioteca para poder lidar com erros:
```zsh
npm i express-async-errors@3.1.1
```
- Agora dentro da pasta `src`, vamos criar uma pasta com o nome de `utils`e dentro dessa pasta vamos criar o arquivo `AppError.ts`, nesse arquivo fazemos o seguinte:
```ts
// AppError.ts

class AppError {
	message: string
	statusCode: number

	constructor(message: string, statusCode: number = 400) {
		this.message = message
		this.statusCode = statusCode
	}
}

export { AppError }
```
- Agora vamos criar uma nova pasta dentro da pasta `src`, com o nome de `middlewares`, e dentro dela vamos criar o arquivo `errorHandling.ts` e dentro dele fazemos o seguinte:
```ts
import { AppError } from "@/utils/AppError"
import { ErrorRequestHandler } from "express"
```
- E agora antes de continuar vamos fazer a instalação do `zod`, para poder fazer validações, para isso usamos o comando:
```zsh
npm i zod@3.24.1
```
- Voltando ao arquivo `errorHandling`:
```ts
import { AppError } from "@/utils/AppError"
import { ErrorRequestHandler } from "express"
import { ZodError } from "zod"

export const errorHandling: ErrorRequestHandler = (error, request, response, next) => {
	if(error instanceof AppError) {
		response.status(error.statusCode).json({ message: error.message})
		return
	}

	if(error instanceof ZodError) {
		response.status(400).json({
			message: "validation error",
			issues: error.format()
		})
		return
	}


	response.status(500).json({ message: error.message })
	return
	
}
```
- Agora para usar, vamos no arquivo `app.ts`, e fazemos a importação do `errorHandling`
```ts
import { errorHandling } from "@/middlewares/errorHandling"

// Adicionamos o trecho abaixo após as rotas
app.use(errorHandling)
```
- Também precisamos fazer a importação do `express-async-errors`, no arquivo `app.ts`
```ts
import 'express-async-errors'
```