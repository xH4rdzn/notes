___
- *ORM* -> Object Relational Mapper
- Para instalar o `prisma`, vamos usar o comando:
```zsh
npm i prisma -D
```
- E para inicializar usamos o comando:
```zsh
npx prisma init
```
- Irá ser gerado uma pasta com o nome de `prisma`e um arquivo com o nome de `schema.prisma`, nesse arquivo vamos criar as nossas tabelas, como no exemplo abaixo:
```prisma
model User {
	id String @id @default(uuid())
	name String
	email String @unique
	@@map("users")
}
```
- Agora para usamos o comando abaixo, para fazer a integração do prisma com o typescript:
```zsh
npx prisma generate
```
- E agora instalamos o que realmente vamos usar em produção:
```zsh
npm i @prisma/client
```
- E agora para fazermos o uso precisamos fazer uma instancia do `@prisma/client`, da seguinte maneira:
```ts
import { PrismaClient } from '@prisma/client'

const prisma = new PrismaClient()


// usando
prisma.user.create({
	data: {
		name: 'Igor',
		email: 'igor@email.com',
	}
})
```