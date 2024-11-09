___
- Para popular o nosso banco de dados, podemos fazer um `seed`, para fazermos isso, vamos seguir os passos:
1. Dentro da pasta `prisma`, vamos criar um arquivo com o nome de: `seed.ts`
2. Dentro desse arquivo vamos seguir o exemplo de código:
```ts
import { prisma } from "@/prisma"

async function seed(){

	await prisma.user.createMany({
		data: [
			{
				name: "Igor Coelho",
				email: "igor@email.com"
			},
			{
				name: "Diego Fernandes",
				email: "diego@email.com"
			},
			// Podemos ter quantos registros quisermos...
		]
	})
}
seed().then(() => {
	console.log("Database Seeded!"))
	prisma.$disconnect()
}
```
- O método `createMany`, serve para criar vários registros de uma vez em uma tabela do banco de dados;
3. Agora vamos no arquivo `package.json`,e vamos adicionar o seguinte script:
```json
"prisma": {
	"seed": "tsx prisma/seed.ts"
},
```
4. Agora para executar esse arquivo, usamos o seguinte comando:
```zsh
npx prisma db seed
```
