____
- Agora vamos organizar a estrutura de pastas do nosso projeto;
- Então dentro da pasta `src`, vamos criar a pasta `routes`e dentro dessa pasta `routes` vamos criar o arquivo `index.ts`;
![[Pasted image 20250203213432.png]]
- E ainda dentro dessa pasta, vamos ter as rotas separadas por arquivos, como por exemplo o `productsRoutes.ts`, que é o arquivo que vai ser responsável pelas rotas de produto:
![[Pasted image 20250203213628.png]]
- Agora dentro dos arquivos de rota, podemos fazer da seguinte forma:
```ts
import { Router } from "express"

const productsRoutes = Router()

productsRoutes.get('/', () => {})

export { productsRoutes }
```
- Após isso, na pasta `src`, podemos criar a pasta `controllers`
![[Pasted image 20250203213857.png]]
- Na pasta `controllers`, vamos criar o arquivo `productsController` e dentro desse arquivo fazemos da seguinte maneira:
```ts
import { Request, Response, NextFunction } from "express"

class ProductController {
	async index(request: Request, response: Response, next: NextFunction) {

		try {

			return response.json({ message: "Ok"})
		} catch (error) {
			next(error)
		}
	}

}

export { ProductController }
```
- Agora voltamos ao arquivo `productsRoutes.ts`e importamos o nosso controller de produtos e usamos como no exemplo abaixo:
```ts
import { Router } from "express"

const productsRoutes = Router()
const productsController = new ProductController()

productsRoutes.get('/', productsController.index)

export { productsRoutes }
```
- Agora precisamos por essas rotas no arquivo `index`das rotas, para isso voltamos ao arquivo `index.ts`, que está dentro da pasta `routes`e fazemos como no exemplo abaixo:
```ts
import { Router } from 'express'
import { productsRoutes } from './productsRoutes'


const routes = Router()

routes.use('/products', productsRoutes)

export { routes }
```
- Agora precisamos passar todas as rotas para o nosso servidor, para isso vamos importar o arquivo `index.ts`da pasta `routes`, no arquivo `server.ts`, como demostrado no exemplo abaixo:
```Ts
import { routes } from "./routes"

app.use(routes)
```
- Desta maneira todas as rotas que estiverem no arquivo `index.ts`da pasta `routes`, vão ficar disponíveis em nossa aplicação;
