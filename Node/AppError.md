___
- Podemos dividir as exceções em dois grupos
	- Erro do cliente -> `bad request`, `status code` 400
	- Erro do servidor -> `Internal Server Error`,`status code` 500
- Para podermos separar vamos fazer da seguinte maneira:
1. Dentro da pasta `src`, vamos criar uma pasta `utils`
2. Dentro da pasta `utils`, vamos criar o arquivo `AppError.ts`
```ts
export class AppError {
	message: string
	statusCode : number

	constructor(message: string, statusCode : number = 400) {
		this.message = message
		this.statusCode = statusCode
	}
}
```
3. E agora vamos utilizar essa classe, sempre que quisermos lançar exceções  no nossos `controllers`.
4. No nosso arquivo `server.ts`, alteramos o código da ultima função que foi criada para tratar os erros
```ts
app.use((error: any, request: Request, response: Reponse, _: NextFunction) => {
	if(error instanceof AppError) {
		return reponse.status(error.statusCode).json({message: error.message})
	}

	reponse.status(500).json({message: error.message})
})
```