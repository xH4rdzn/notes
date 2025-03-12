___
- Para criar uma tabela usamos o comando:
```zsh
npm run knex -- migrate:make create-tables
```
- No arquivo gerado, podemos seguir o exemplo:
```Ts
export async function up(knex: Knex): Promise<void> {
	await knex.schema.createTable("tables", (table) => {
		table.increments("id").primary(),
		table.integer("table_number").notNullable(),
		table.timestamp("created_at").defaultTo(knex.fn.now())
		table.timestamp("updated_at").defaultTo(knex.fn.now())
	})
}
```
- E na função `down`, fazemos a reversão dessa migration, no caso só apagar a tabela, como no exemplo:
```ts
export async function down(knex: Knex): Promise<void> {
	await knex.schema.dropTable("tables")
	})
}
```
- E para acrescentar essa migration em nosso banco de dados, usamos o comando:
```zsh
npm run knex -- migrate:latest 
```