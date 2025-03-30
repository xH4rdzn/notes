___
- Agora podemos cadastrar essas informações no banco de dados
```ts
import { prisma } from "@/database/prisma"
import { AppError } from "@/utils/AppError"
import { Request, Response } from 'express'
import { z } from 'zod'

const CategoriesEnum = z.enum([
	"food",
	"others",
	"services",
	"transport",
	"accommodation"
])

class RefundsController {
	async create(request: Request, response: Response){
		const bodySchema = z.object({
			name: z.string().trim().min(1, { message: "Informe o nome da solicitação"}),
			category: CategoriesEnum,
			amount: z.number().positive({message: "O valor precisa ser positivo"}),
			filename: z.string().min(20),
		})
		
		const { name, category, amount, filename } = bodySchema.parse(request.body)

		if(!request.user?.id) {
			throw new AppError("Não autorizado", 401)
		}
		
		const refund = await prisma.refunds.create({
			data: {
				name,
				category,
				amount,
				filename,
				userId: request.user.id
			}
		})
		
		return response.status(201).json(refund)
	}
}

export { RefundsController}
```