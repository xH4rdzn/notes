___
- Anteriormente criamos o [[Teste no Cadastro do Usuário]], mas se rodarmos o teste novamente ele irá falhar, pois ele não vai deixar criar o mesmo usuário que já foi cadastrado.
- Então para garantir que esse teste rode de uma maneira correta, temos que garantir que esse usuário de teste não exista no banco de dados, para fazer isso vamos alterar o nosso teste para:
```ts
import request from "supertest"
import { prisma } from "@/database/prisma"

import { app } from "@/app"

describe("UsersController", () => {
	let user_id: string

	afterAll( async () => {
		await prisma.user.delete({ where: { id: user_id } })
	})

	it("should create a new user sucessfully", async () => {
		const response = await request(app).post("/users").send({
			name: "Test User",
			email: "testuser@example.com",
			password: "password123",
		})

		expect(response.status).toBe(201)
		expect(response.body).toHaveProperty("id")
		expect(response.body.name).toBe("Test User")

		user_id = response.body.id
	})
})
```
- Desta maneira ao finalizar o teste, ele irá apagar o usuário criado pelo teste.