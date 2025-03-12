___
- Vamos criar várias mesas com o `seed`, para isso vamos usar o comando:
```zsh
npm run knex -- seed:make insert-tables
```
- No arquivo gerado vamos fazer o seguinte:
```ts
export async function seed(knex: Knex): Promise<void> {
	await knex("tables").del()

	await knex("tables").insert([
		{ table_number: 1 },
		{ table_number: 2 },
		{ table_number: 3 },
		{ table_number: 4 },
		{ table_number: 5 }
	])
}
```
- E agora usamos o comando:
```zsh
npm run knex -- seed:run
```
- Para popular com os dados a nossa tabela.