___
- Agora vamos criar um método para encerrar a sessão da mesa
```ts
async update(request: Request, response: Response, next: NextFunction) {
	try {
		const id = z
		 .string()
		 .transform((value) => Number(value))
		 .refine((value) => !isNaN(value), { message: "id must be a number"})
		 .parse(request.params.id)


		return response.json()
	} catch(error){
		next(error)
	}
}
```
- Agora em nosso arquivo de rotas, adicionamos:
```ts
tablesSessionsRoutes.patch("/:id", tablesSessionsController.update)
```
- Desta maneira já estamos validando o `id`, da sessão e já temos a rota disponível;
