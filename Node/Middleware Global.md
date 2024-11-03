___
- Com o `express`, podemos criar middlewares e usar de maneira global e maneira local.
- Para criar um middleware, de maneira organizada, em nossa aplicação, dentro da pasta `src`, vamos criar uma nova pasta com o nome de `middlewares`, e dentro dessa pasta vamos criar os nossos middlewares.
- Como o middleware é uma função, precisamos criar ela da seguinte maneira:
```ts
export function myMiddleware(request, reponse) {}
```
- Agora precisamos passar os tipos para o `request` e o `response`, e para fazermos isso, importamos as tipagens do `express`:
```ts
import { Request, Response } from "express"
```
- E passamos eles para o nosso middleware:
```ts
export function myMiddleware(request: Request, reponse: Response) {}
```
- Mas como estamos trabalhando com middlewares, temos que usar também o `next`, que é responsável por chamar a próxima função, caso contrário nossa requisição irá morrer no middleware; Então passamos esse parâmetro da seguinte maneira:
```ts
export function myMiddleware(request: Request, reponse: Response, next) {}
```
- E importamos a tipagem dele de dentro do `express`:
```ts
import { Request, Response, NextFunction } from "express"
```
- E agora passamos o tipo para a nossa função:
```ts
export function myMiddleware(request: Request, reponse: Response, next: NextFunction) {}
```
- Agora temos acesso a todos os métodos de `request` e `response`.
- E agora podemos criar o código do nosso middleware, mas como é apenas um exemplo, vou apenas fazer um `console.log` e fazer seu retorno
```ts
export function myMiddleware(request: Request, reponse: Response, next: NextFunction) {

	console.log("Passou pelo middleware")


	return next()
}
```
- Precisamos retornar o `next()`, para chamar a próxima função.
- Agora para passar esse middleware de maneira global, ou seja, aplicar esse middleware para todas as rotas, passamos ele da seguinte maneira:
```ts
app.use(myMiddleware)
// código das rotas abaixo
```
- Precisamos passar o middleware antes do código das rotas.