___
- Dentro da pasta `src`, vamos criar duas pastas novas:
	- `routes` -> pasta onde irá conter os nossos arquivos de rotas;
	- `controllers`-> pasta dos nossos *controllers*;
- Dentro da pasta `controllers`, vamos criar o arquivo `usersController.ts`, e dentro desse arquivo vamos criar uma classe, como no exemplo abaixo:
```ts
import { Request, Response } from "express"
class UsersController {
	create(request: Request, response: Response) {
		return response.json({ message: "ok"})
	}
	
}

export { UsersController}
```
- Agora dentro da pasta `routes`, vamos criar o arquivo `usersRoutes.ts`, e dentro desse arquivo fazemos o seguinte:
```ts
import { Router } from "express"
import { UsersController } from "@/controllers/usersController"

const usersRoutes = Router()
const usersController = new UsersController()

usersRoutes.post("/", usersController.create)


export { usersRoutes }
```
- Ainda dentro da pasta `routes`, vamos criar o arquivo `index.ts`, para podermos centralizar todas as rotas da nossa aplicação, dentro desse arquivo fazemos o seguinte:
```Ts
import { Router } from "express"

import { usersRoutes } from "./usersRoutes"

const routes = Router()
routes.use("/users", usersRoutes)

export { routes }
```
- Agora no nosso arquivo `app.ts`, importamos o arquivo `routes`e adicionamos a seguinte linha:
```ts
// Importando o arquivo routes
import { routes } from "./routes"

// Passando para o app
app.use(routes)
```