___
- No arquivo `schema.prisma`, vamos criar as nossas tabelas do banco de dados.
```prisma
model User {
	id String @id @default(uuid())
	name String
	email String @unique
	password String
	created_at DateTime @default(now())
	
}

model CheckIn {
	id String @id @default(uuid())
	created_at DateTime @default(now())
	validated_at DateTime?

	@@map("check_ins")
}

model Gym {
	id String @id @default(uuid())
	title String
	description String?
	phone String?
	latitude Decimal
	longitude Decimal
	

	@@map("gyms")
}
```