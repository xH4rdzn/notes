___
- Vamos criar essa tabela no banco de dados para controlar o status das mesas do restaurante;
- Para criar a `migration`, usamos o comando:
```zsh
npm run knex -- migrate:make create-tables-sessions
```
- Agora no arquivo da `migration`, vamos fazer o seguinte:
```Ts
export async function up(knex: Knex): Promise<void> {
	await knex.schema.createTable("tables_sessions", (table) => {
		table.increments("id").primary(),
		table.integer("table_id").notNullable().references("id").inTable("tables")
	table.timestamp("opened_at").defaultTo(knex.fn.now())m
	table.timestamp("closed_at")
	})
}


export async function down(knex: Knex) {
	await knex.schema.dropTable("tables_sessions")
}
```
- Agora para executar essa `migration`, usamos o comando:
```zsh
npm run knex -- migrate:latest
```
