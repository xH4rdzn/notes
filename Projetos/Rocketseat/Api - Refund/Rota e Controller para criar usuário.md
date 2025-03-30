___
- Agora dentro da pasta `src`, vamos criar a pasta `controllers`e dentro dessa pasta vamos criar o `usersController.ts` e dentro desse arquivo vamos fazer o seguinte:
```ts
import { Request, Response } from 'express'

class UsersController {
	async create(request: Request, response: Response) {
		return response.json({ message: "ok"})
	}
}

export { UsersController }
```
- Agora dentro de `src`, vamos criar a pasta `routes`, e dentro dessa pasta vamos criar o arquivo `usersRoutes.ts`e dentro desse arquivo vamos fazer:
```ts
import { Router } from 'express'

import { UsersController } from "@/controllers/usersController"

const usersRoutes = Router()
const usersController = new UsersController()

usersRoutes.post("/", usersController.create)


export { usersRoutes }
```
- Agora dentro da pasta `routes`, vamos criar o arquivo `index.ts` e dentro dele vamos fazer o seguinte:
```ts
import { Router } from 'express'
imporrt { usersRoutes } from "./usersRoutes"

const routes = Router()

routes.use("/users", usersRoutes)

export { routes }
```
- Agora vamos ao arquivo `app.ts`, e adicionamos o seguinte:
```ts
import { routes } from "./routes"

// após o `express.json()` adicionamos:
app.use(routes)

```
- Agora podemos criar uma rota no `Insomnia`para poder testar;