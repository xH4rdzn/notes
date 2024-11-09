___
- Como já vimos em [Criando Tabela com Prisma](./Criando%20Tabela%20com%20Prisma.md), mas agora vamos criar a tabela de Perguntas, nelas vamos ver alguns pontos diferentes e como fazemos no prisma
```prisma
model Question {
	id String @id @default(uuid())
	title String
	content String

	createdAt DateTime @default(now()) @map("created_at")
	updatedAt DateTime @updatedAt

	userId String @map("user_id")

	@@map("questions")
}
```
- Para datas usamos o tipo `DateTime`;
- O `@map`, serve para darmos um nome de como essa coluna vai ficar no banco de dados;
- O `@updatedAt`, ele identifica automaticamente quando alteramos o registro e já modifica a data e a hora;
- Agora que já aprendemos a manipular datas, só precisamos ver como funciona os [Relacionamentos no prisma](./Relacionamentos%20no%20prisma.md);
