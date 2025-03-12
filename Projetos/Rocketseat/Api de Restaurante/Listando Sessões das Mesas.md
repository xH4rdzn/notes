___
- Agora vamos criar uma rota para poder listar todas as mesas que estão abertas:
```ts
async index(request: Request, response: Response, next: NextFunction) {
	try {
		const sessions = await knex<TablesSessionsRepository>("tables_sessions").orderBy("closed_at")
		return response.json(sessions)
	} catch(error) {
		next(error)
	}
}
```
- Agora vamos no arquivo de rotas e adicionamos:
```Ts
tablesSessionsRoutes.get('/', tablesSessionsController.index)
```