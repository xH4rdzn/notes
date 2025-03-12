___
- Vamos criar um novo `controller`, para as mesas, vamos chamar ele de `tablesController.ts`
- E dentro dele vamos fazer o seguinte:
```ts
import { Request, Response, NextFunction } from "express"

export class TablesController {
	async index(request: Request, response: Response, next: NextFunction) {
		try {
			const tables = await knex("tables").select().orderBy("table_number") 
		} catch (error) {
			next(error)
		}
	}
}
```
- Agora vamos criar uma tipagem para essa tabela;
- Dentro da pasta `types`que está dentro da pasta `database`, vamos criar o arquivo `tableRepository.d.ts`, e vamos escrever o seguinte código dentro dela:
```ts
type TableRepository = {
	id: number
	table_number: number
	created_at: number
	updated_at: number
}
```
- Agora passamos a tipagem para o nosso controller da seguinte maneira:
```ts
import { Request, Response, NextFunction } from "express"

export class TablesController {
	async index(request: Request, response: Response, next: NextFunction) {
		try {
			const tables = await knex<TableRepository>("tables").select().orderBy("table_number") 

			return response.json(tables)
		} catch (error) {
			next(error)
		}
	}
}
```
- Agora vamos criar um arquivo para criar as rotas da mesa, para isso vamos criar o arquivo `tablesRoutes`, dentro da pasta `routes`e vamos fazer o seguinte:
```ts
import { Router } from "express"

import { TablesController } from "@/controllers/tablesController"

const tablesRoutes = Router()
const tablesController = new TablesController()

tablesRoutes.get('/', tablesController.index)

export { tablesRoutes }
```
- Agora vamos no arquivo `index.ts`, que está dentro da pasta `routes`e adicionamos esse arquivo da seguinte maneira:
```Ts
routes.use("/tables", tablesRoutes)
```
- Agora basta testarmos no `Insomnia`;