___
- Dentro da pasta `src`, vamos criar uma nova pasta com o nome de `middlewares`;
- Dentro da pasta `middlewares`, vamos criar o arquivo `errorHandling.ts`;
- Dentro desse arquivo vamos escrever o seguinte código:
```ts
import { Request, Response, NextFunction } from "express"

export function errorHandling(
	error: any,
	request: Request,
	response: Response, 
	next: NextFunction
	) {
	
}
```
- Antes de continuarmos o nosso `middleware`, vamos criar uma classe para tratar exceções que são lançadas pela nossa aplicação, para isso vamos criar dentro de `src`a pasta `utils` e dentro dela vamos criar o arquivo `AppError.ts`;
- Dentro do arquivo `AppError.ts`, vamos criar o seguinte código:
```ts
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
- Agora voltamos ao nosso `middleware` o `errorHandling`e fazemos da seguinte maneira:
```ts
import { Request, Response, NextFunction } from "express"
import { AppError } from "@/utils/AppError"

export function errorHandling(
	error: any,
	request: Request,
	response: Response, 
	next: NextFunction
	) {
		if(error instanceof AppError) {
			return response.status(error.statusCode).json({ message: error.message})
		}
		return response.status(500).json({message: error.message})
}
```
- Agora para utilizarmos o nosso `middleware`, vamos instalar uma biblioteca, com o comando:
```zsh
npm i express-async-errors
```
- Agora em nosso arquivo `app.ts`, apenas importamos a biblioteca que acabamos de instalar
```ts
import "express-async-errors"
```
- E agora fazemos a importação do nosso `middleware`
```ts
import { errorHandling } from "@/middlewares/errorHandling"
```
- E logo após, onde declaramos para o `express`, que ele vai utilizar o formato `json`, adicionamos o nosso `middleware`
```ts
app.use(errorHandling)
```