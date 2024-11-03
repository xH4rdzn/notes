___
- Para poder inserir dados no nosso banco de dados, primeiro precisamos configurar a conexão da nossa aplicação com o nosso banco de dados. Para isso vamos seguir os passos abaixo:
1. Dentro da pasta `database`, vamos criar o arquivo: `knex.ts`
2. Dentro desse arquivo vamos fazer o seguinte código:
```ts
import { knex as knexConfig } from "knex"
import config from "../../knexfile"

export const knex = knexConfig(config)
```
3. Agora voltamos ao local onde está nossa rota de `post`, e importamos o arquivo que criamos no passo anterior:
```ts
import { knex } from "./database/knex"

app.post("/courses", async (request: Request, response: Response) => {
	const { name } = request.body

	await knex("courses").insert({ name })

	response.status(201).json()
})
```
- Lembrando que a função precisa ser `async`, pois precisamos aguardar o banco de dados;
- Usamos `await` na função do `knex`, como parâmetro da função `knex`, passamos a qual tabela vamos inserir, e logo após usamos o método `insert`, nesse método passamos um objeto com quais dados queremos inserir;