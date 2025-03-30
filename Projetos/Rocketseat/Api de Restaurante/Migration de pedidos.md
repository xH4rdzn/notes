___
- Vamos criar uma nova *migration*, com o comando:
```zsh
npm run knex -- migrate:make create-orders
```
- Assim na pasta *migrations*, irá aparecer um novo arquivo, nesse arquivo vamos fazer da seguinte maneira:
```ts
import type { Knex } from "knex";

export async function up(knex: Knex): Promise<void> {
	await knex.schema.createTable('orders', (table) => {
		table.increments("id").primary(),
		table.integer("tables_session_id").notNullable().references("id").inTable("tables_sessions"),
		table.integer("product_id").notNullable().references("id").inTable("products"),
		table.integer("quantity").notNullable(),
		table.decimal("price").notNullable(),
		table.timestamp("created_at").defaultTo(knex.fn.now()),
	table.timestamp("updated_at").defaultTo(knex.fn.now())
	})
}

export async function down(knex: Knex): Promise<void> {
	await knex.schema.dropTable("orders")
}
```
- Agora executamos essa *migration* com o comando:
```zsh
npm run knex -- migrate:latest
```