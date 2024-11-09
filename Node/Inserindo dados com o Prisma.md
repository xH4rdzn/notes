___
- Para usar o prisma para fazer alterações no nosso banco de dados, fazemos como descrito nos passos abaixo, porém essa é uma forma mais simples, apenas para demonstrar de como fazer seu uso;
1. Dentro da pasta `src`, vamos criar um arquivo com o nome: `prisma.ts`
2. Dentro desse arquivo vamos escrever o seguinte código:
```ts
import { PrismaClient } from "@prisma/client"

export const prisma = new PrismaClient({
	log: ["query"],
})
```
3. Agora para fazer o uso dessas configurações, voltamos ao nosso controller e o importamos:
```ts
import { prisma } from "@/prisma"
```
4. Agora podemos usar o `prisma`, e para inserir dados, como no exemplo abaixo:
```ts
async create(request: Request, response: Response) {
	const { name, email } = request.body

	await prisma.user.create({data: { name, email }})

	return response.status(201).json()
}
```
- Após acessar a rota com o método `POST`, e passarmos os dados no `Body Request`, esses dados irão ser cadastrados no banco de dados;
- Podemos visualizar o usuário cadastrado no `Primsa Studio`;