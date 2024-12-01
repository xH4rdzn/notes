___
- Como vimos anteriormente [[Criando Tabela com Prisma|anteriormente]], para criar as tabelas com o prisma, vamos criar as tabelas de `User`
- Podemos também criar `enum's`, para definir algumas caracteristicas, como o `role`, que só temos duas opções ou é `customer`ou é `sale`
*Criando um enum no prisma*
```prisma
enum UserRole {
	customer
	sale
}
```
- Então a tabela de usuários irá ficar desta maneira:
*User*
```prisma
model User {
	id String @id @default(uuid())
	name String
	email String
	password String
	role UserRole @default(customer)
	createdAt DateTime @default(now()) @map("created_at")
	updatedAt DateTime? @updatedAt @map("updated_at")

	@@map("users")
}
```
- Para o `updatedAt`, passamos o `?`, pois ele é opcional e também passamos o `@updatedAt`, para gravar essa data apenas quando for atualizado o registro.
- Já a nossa tabela de entregas, que se relaciona com a tabela `User`, vai ficar da seguinte maneira:
```prisma
model Delivery {
	id String @id @default(uuid())
	userId String @map("user_id")
	description String
	status DeliveryStatus @default(processing)
	createdAt DateTime @default(now()) @map("created_at")
	updatedAt DateTime? @updatedAt @map("updated_at")

	user User @relation(fields: [userId], references: [id])

	@@map("deliveries")

}
```
- E ele pede para fazermos a indicação do relacionamento na outra tabela também, então devemos alterar a nossa tabela de `User`para:
```prisma
model User {
	id String @id @default(uuid())
	name String
	email String
	password String
	role UserRole @default(customer)

	deliveries Delivery[]

	createdAt DateTime @default(now()) @map("created_at")
	updatedAt DateTime? @updatedAt @map("updated_at")

	@@map("users")

}
```
- Nota-se que passamos `deliveries Delivery[]`, isso indica que um usuário pode ter muitas entregas.
- Se fosse um relacionamento de 1:1 seria: `deliveries Delivery`, podemos ver mais em [[Relacionamentos no prisma]]
-  Já a nossa tabela de `logs`, que vão indicar o status da entrega vai ficar da seguinte maneira:
```prisma
model DeliveryLog {
	id String @id @default(uuid())
	description String
	deliveryId String @map("delivery_id")

	delivery Delivery @relation(fields: [deliveryId], references: [id])

	createdAt DateTime @default(now()) @map("created_at")
	updatedAt DateTime? @updatedAt @map("updated_at")

	@@map("delivery_logs")

}
```
- Como temos um relacionamento com a tabela `Delivery`, precisamos altera-lá, deixando a tabela `Delivery`da seguinte maneira:
```prisma
model Delivery {

	id String @id @default(uuid())
	userId String @map("user_id")
	description String
	status DeliveryStatus @default(processing)
	createdAt DateTime @default(now()) @map("created_at")
	updatedAt DateTime? @updatedAt @map("updated_at")

	user User @relation(fields: [userId], references: [id])
	logs DeliveryLog[]

	@@map("deliveries")
}
```
