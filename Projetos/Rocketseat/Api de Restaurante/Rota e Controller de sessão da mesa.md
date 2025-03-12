___
- Para isso vamos criar um novo `controller`, vamos criar o `tablesSessionsController.ts`, e vamos seguir o exemplo:
```ts
import { Request, Response, NextFunction } from "express"

export class TablesSessionsController {
	async create(request: Request, response: Response, next: NextFunction) {
		try {
		 return response.status(201).json()
		} catch(error){
			next(error) 
		}
	}
}
```
- Agora vamos criar um novo arquivo para adicionar essas rotas, vamos chamar ele de `tablesSessionsRoutes`
```ts
import { Router } from "express"

import { TablesSessionsController } from "@/controllers/tablesSessionsController"

const tablesSessionsRoutes = Router()
const tablesSessionsController = new tablesSessionsController()


tablesSessionsRoutes.post("/", tablesSessionsController.create)

export { tablesSessionsRoutes }

```
- Agora no arquivo `index.ts`, vamos adicionar:
```ts
routes.use("tables-sessions", tablesSessionsRoutes)
```
