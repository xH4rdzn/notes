___
- Para formatar as mensagens de erro do `zod`, no código onde estamos capturando e tratando essa exceção, adicionamos o seguinte pacote e validação:
- Pacote:
```ts
import { ZodError } from "zod"
```
- Validação
```ts
app.use((error: any, request: Request, response: Reponse, _: NextFunction) => {
	if(error instanceof AppError) {
		return reponse.status(error.statusCode).json({message: error.message})
	}

	// Validação a ser adicionada
	if(error instanceof ZodError) {
		return response.status(400).json({message: "Validation error!", issues: error.format()})
	}

	reponse.status(500).json({message: error.message})
})
```
