___
- Agora que [[Validando dados do usuário refund|validamos os dados do usuário]], podemos fazer o cadastro dele no nosso banco de dados:
```ts
import { Request, Response } from 'express'
import { z } from 'zod'
import { UserRole } from '@prisma/client'
import { prisma } from "@database/prisma"
import { hash } from 'bcrypt'

class UsersController {
	async create(request: Request, response: Response) {
		const bodySchema = z.object({
			name: z.string().trim().min(2, { message: "Nome é obrigatório"}),
			email: z.string().trim().email({ message: "E-mail inválid"}).toLowerCase(),
			password: z.string().min(6, { message: "A senha deve ter pelo menos 6 caracteres"}),
			role: z.enum([UserRole.employee, UserRole.manager]).default(UserRole.employee),
		})

		const { name, email, password, role } = bodySchema.parse(request.body)

		// Recuperando o usuário pelo e-mail
		 const userWithSameEmail = await prisma.user.findFirst({ where : { email } })

		// Verificando se já existe um email cadastrado no banco, se existir retorna um erro
		if(userWithSameEmail) {
			throw new AppError('Já existe um usuário cadastrado com esse e-mail')
		}

		// Criptografando a senha
		const hashedPassword = await hash(password, 8)

		// Cadastrando o usuário no banco
		await prisma.user.create({
			data: {
				name,
				email,
				password: hashedPassword,
				role,
			}
		})

		return response.status(201).json()
	}
}

export { UsersController }
```
- Para poder fazermos a criptografia da senha, vamos instalar o `bcrypt`, para isso vamos usar o comando:
```zsh
npm i bcrypt
```
- E também vamos instalar suas tipagens:
```zsh
npm i @types/bcrypt -D
```
- Agora voltamos ao nosso controller