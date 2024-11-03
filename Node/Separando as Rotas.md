___
- Vamos separar as rotas da nossa aplicação, da seguinte maneira:
1. Dentro da pasta `src`, vamos criar uma pasta com o nome de `routes`
2. Dentro da pasta `routes`, vamos criar um arquivo relacionado a cada rota. Como exemplo vamos criar um arquivo relacionado a rota de produtos, então o nome do arquivo vai ser `products-routes.ts`.
3. Dentro do arquivo criado, vamos importar o `Router` do `express`
```ts
import { Router } from "express" 
```
4. E vamos usar da seguinte maneira:
```ts
import { Router } from "express"

const productsRoutes = Router()

productsRoutes.get("/products", (request, response) => {
	// Código da função que é executada ao acessar a rota.
})

productsRoutes.post("/products", (request, response) => {
	// Código da função que é executada ao acessar a rota.
})

export { productsRoutes }
```
5. Dentro da pasta `routes`, vamos criar um arquivo `index.ts`
6. Dentro desse arquivo vamos por todas as nossas rotas da aplicação.
7. Vamos usar da seguinte maneira:
```ts
import { Router } from "express"

import { productsRoutes } from "./products-routes"

const routes = Router()

// Primeiro parâmetro é o endereço que vai ser usado para as rotas
// Segundo parâmetro é o arquivo onde vai estar as nossas rotas
routes.use("/products", productsRoutes)
```
8. Voltamos ao arquivo `products-routes`, e só alteramos o endereço para não ter conflito
9. E importamos no arquivo `server.ts` e importamos e usamos o arquivo de rotas.
```ts
import { routes } from "./routes"


app.use(routes)
```
