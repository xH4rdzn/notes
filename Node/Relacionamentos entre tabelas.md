___
- Como anteriormente criamos as nossas tabelas [[Criando schema do Prisma|no schema do prisma]], agora precisamos fazer o relacionamento entre elas.
```prisma
model User {
	id String @id @default(uuid())
	name String
	email String @unique
	password String
	created_at DateTime @default(now())
	checkIns CheckIn[]
}

model CheckIn {
	id String @id @default(uuid())
	created_at DateTime @default(now())
	validated_at DateTime?

	user User @relation(fields: [user_id], references: [id])
	user_id String

	gym Gym @relation(fields: [gym_id], references: [id])
	gym_id String
	
	@@map("check_ins")
}

model Gym {
	id String @id @default(uuid())
	title String
	description String?
	phone String?
	latitude Decimal
	longitude Decimal
	checkIns CheckIn[]

	@@map("gyms")
}
```