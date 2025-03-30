___
- Agora dentro do arquivo `schema.prisma`
```prisma
enum UserRole {
	employee
	manager
}

enum Category {
	food
	others
	services
	transport
	accommodation
}

model User {
	id String @id @default(uuid())
	name String
	email String @unique
	password String

	role UserRole @default(employee)

	refunds Refunds[]

	createdAt DateTime @default(now()) @map("created_at")
	updatedAt DateTime? @updatedAt @map("updated_at")

	@@map("users")
}

model Refunds {
	id String @id @default(uuid())
	name String
	amount Float
	category Category
	filename String

	userId String @map("user_id")
	user User @relation(fields: [userId], references: [id])

	createdAt DateTime @default(now()) @map("created_at")
	updatedAt DateTime? @updatedAt @map("updated_at")

	@@map("refunds")
}
```
- Agora para rodar essa migration, usamos o comando:
```zsh
npx prisma migrate dev --name create_tables
```