___
- Voltando ao nosso [[Criando controller e rota de autenticação refund|controller de autenticação]], adicionamos:
```ts
import { Request, Response } from 'express'
import { z } from 'zod'

class SessionsController {
	async create(request: Request, response: Response) {
		const bodySchema = z.object({
			email: z.string().email({ message: 'E-mail inválido'}),
			password: z.string(),
		})

		const { email, password } = bodySchema.parse(request.body)

		
		
		response.json({ message: "ok"})
	}
}

export { SessionsController }
```