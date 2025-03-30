___
- Agora que já [[Salvando o pedido|estamos adicionando itens no pedido]], podemos listar os itens que foram solicitados por uma mesa
- Voltamos ao nosso *Orderscontroller* e criamos um novo método
```ts
async index(request: Request, response: Response, next: NextFucntion) {
	try {
		
		return response.json()
	} catch(error) {
		next(error)
	}
}
```
- E agora no arquivo de rotas dos pedidos `ordersRoutes.ts`, adicionamos:
```ts
ordersRoutes.get("/table-session/:table_session_id", ordersController.index)
```
- Desta maneira já temos a rota disponibilizada em nossa aplicação;