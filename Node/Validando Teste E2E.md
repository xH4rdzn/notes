___
- Anteriormente [[Executando Teste E2E|criamos o nosso teste E2E]], mas ainda não validamos, para validarmos esse teste, vamos fazer da seguinte maneira:
```ts
import request from "supertest"
import { app } from "./app"

describe("products", () => {
	it("should list products", async () => {
		const response = await request(app).get("/products")

		expect(response.statusCode).toBe(200)
		expect(response.body).toHaveLength(3)
		expect(response.body.length).toBeGreaterThan(0)
	})
})
```
*Podemos acumular os `expect`, para verificar se está devolvendo a resposta que queremos;