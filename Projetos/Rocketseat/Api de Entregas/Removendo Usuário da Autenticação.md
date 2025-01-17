___
- Para podermos remover o usuário criado para testar a autenticação, podemos adicionar no teste de autenticação o seguinte código:
```ts
afterAll(async () => {
	await prisma.user.delete({ where: { id: user_id} })
})
```
- E também devemos fazer a importação do `prisma`
```ts
import { prisma } from "@/database/prisma"
```