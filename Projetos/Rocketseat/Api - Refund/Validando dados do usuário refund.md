___
- Ainda dentro do nosso [[Rota e Controller para criar usuário|controller]], continuamos:
```ts
import { Request, Response } from 'express'
import { z } from 'zod'
import { UserRole } from '@prisma/client'

class UsersController {
	async create(request: Request, response: Response) {
		const bodySchema = z.object({
			name: z.string().trim().min(2, { message: "Nome é obrigatório"}),
			email: z.string().trim().email({ message: "E-mail inválid"}).toLowerCase(),
			password: z.string().min(6, { message: "A senha deve ter pelo menos 6 caracteres"}),
			role: z.enum([UserRole.employee, UserRole.manager]).default(UserRole.employee),
		})

		const { name, email, password, role } = bodySchema.parse(request.body) 
		
		return response.json({ message: "ok"})
	}
}

export { UsersController }
```