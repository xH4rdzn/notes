___
- Agora vamos fazer um teste para testar a autenticação;
- Para fazer criar esse teste dentro da pasta `test`, vamos criar o arquivo `sessionsController.test.ts`.
- Neste arquivo vamos criar o teste da seguinte maneira:
```ts
import request from "supertest"

import { app } from "@/app"

describe("SessionsController", () => {
	let user_id: string

	it("should authenticate a and get acess token", async () => {
		const userResponse = await request(app).post("/users").send({
			name: "Test User",
			email: "authuser@example.com",
			passoword: "password123"
		})

		user_id = userResponse.body.id

		const sessionResponse = await request(app).post("/sessions").send({
			email: "authuser@example.com",
			password: "password123",
		})

		expect(sessionsResponse.status).toBe(200)
		expect(sessionsResponse.body.token).toEqual(expect.any)
	})
})
```