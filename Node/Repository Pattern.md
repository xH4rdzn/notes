___
- O `Repository Pattern`, serve para especificamente para abstrair a parte de conexão de requisição que fazemos para o banco de dados, em um arquivo separado.
- Para utilizar esse *pattern*, dentro da pasta `src`, vamos criar a pasta `repositories` e dentro dele vamos criar o arquivo: `prismaUsersRepository.ts` e dentro desse arquivo vamos fazer o seguinte:
```ts
export class PrismaUsersRepository {
	async create(data) {
		await prisma.user.create({
			data: {
				name,
				email,
				password: passwordHashed
			}
		})
	}
}
```
- Agora para o `data`, podemos reaproveitar a tipagem feita pelo Prisma, para isso vamos alterar o código acima para:
```ts
import { prisma } from '@/lib/prisma'
import { Prisma } from '@prisma/client'

export class PrismaUsersRepository {
	async create(data: Prisma.UserCreateInput) {
		await prisma.user.create({
			data: {
				name,
				email,
				password: passwordHashed
			}
		})
	}
}
```
- Desta maneira o código especifico do `prisma`fica separado em um arquivo, caso futuramente queiramos usar outra ferramenta, fica mais fácil de retirar o código que é relacionado ao prisma. *ESSA É UMA DAS VANTAGENS.*
