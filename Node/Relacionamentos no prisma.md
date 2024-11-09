___
- Para criar um relacionamento em uma tabela, através do prisma, fazemos da seguinte maneira:
```prisma
model Question {
	id String @id @default(uuid())
	title String
	content String

	createdAt DateTime @default(now()) @map("created_at")
	updatedAt DateTime @updatedAt @map("updated_at")

	// Relacionamento
	userId String @map("user_id")
	
	user User @relation(fields: [userId], references: [id])
}
```
- Em `fields`, passamos a coluna dessa tabela que vai conter a chave estrangeira;
- Em `references`, passamos a coluna de onde ele vai pegar da tabela que passamos como tipo;
- Porém ele vai continuar dando erro, pois precisamos dizer na outra tabela na qual ela se relaciona que temos um relacionamento deixando nossa tabela de usuários assim:
```prisma
model User {
	id String @id @default(uuid())
	name String
	email String @unique

	questions Question[]

	@@map("users")
}
```
- Nota-se que estamos fazendo um relacionamento de um para muitos;
- Para fazer um relacionamento de 1:1, a nossa tabela de `User`, ficaria da seguinte maneira:
```prisma
model User {
	id String @id @default(uuid())
	name String
	email String @unique

	questions Question

	@@map("users")
}
```
