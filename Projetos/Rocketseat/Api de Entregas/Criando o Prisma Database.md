___
- Antes de salvarmos o nosso usuário no nosso banco de dados, vamos:
1. Criar uma pasta com o nome `database`, dentro de `src`
2. Dentro da pasta `database`, vamos criar o arquivo com o nome de `prisma.ts`, esse arquivo vai receber as configurações de conexão do banco de dados com o prisma.
```ts
import { PrismaClient } from "@prisma/client"
```
3. E agora podemos exportar uma instancia do `PrismaClient`, da seguinte maneira:
```ts
import { PrismaClient } from "@prisma/client"

export const prisma = new PrismaClient({
	log: ["query"],
})
```
- Podemos fazer uma verificação, para caso a nossa aplicação esteja em ambiente de produção, não exibir os `logs`, para isso podemos alterar o código para:
```ts
import { PrismaClient } from "@prisma/client"

export const prisma = new PrismaClient({
	log: process.env.NODE_ENV === "production" ? [] : ["query"],
})
```