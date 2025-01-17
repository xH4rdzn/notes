___
- Agora vamos implementar o nosso primeiro teste, que é verificar se o cadastro do usuário é realizado com sucesso.
- No arquivo que criamos, `usersController.test.ts`, vamos escrever o seguinte código:
```ts
import request from "supertest"
import { app } from "@/app"

describe("UsersController", () => {
	it("should create a new user successfully", async () => {
		const response = await request(app).post("/users").send({
			name: "Test User",
			email: "testuser@example.com",
			password: "password123",
		})


		expect(response.status).toBe(201)
		expect(response.body).toHaveProperty("id")
	})
})
```
- Agora podemos rodar o comando:
```zsh
npm run test:dev
```
- E será executado o teste