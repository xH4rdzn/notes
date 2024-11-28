___
- Para executarmos testes E2E, vamos usar outra biblioteca, neste caso vamos usar o `supertest`, vamos instalar elas usando o comando abaixo:
```zsh
npm i supertest @types/supertest -D
```
- Vamos criar um arquivo de testes e nesse arquivo, vamos fazer da seguinte maneira:
```ts
import request from "supertest"
import { app } from "./app"

describe("products", () => {
	it("should list products", async () => {
		const response = await request(app).get("/products")

		console.log(response.body)
	})
})
```
*Podemos notar que mesmo sem a nossa aplicação estar rodando, o teste faz uma requisição para a nossa aplicação e devolve o que seria devolvido na rota criada.*