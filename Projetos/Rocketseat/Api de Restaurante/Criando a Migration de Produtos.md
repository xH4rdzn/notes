___
- No arquivo gerado da *migration*, após rodar o comando:
```zsh
npm run knex -- migrate:make create-products
```
- Irá ser gerado um arquivo no local no qual foi configurado pelo arquivo `knexfile.ts`, nesse arquivo para poder criar uma tabela, seguimos o exemplo:
```ts
import type { Knex } from "knex";

export async function up(knex: Knex): Promise<void> {
	await knex.schema.createTable("products", (table) => {
		table.increments("id").primary(),
		table.text("name").notNullable(),
		table.decimal("price").notNullable(),
		table.timestamp("created_at").defaultTo(knex.fn.now())
		table.timestamp("updated_at").defaultTo(knex.fn.now())
	})
}

export async function down(knex: Knex): Promise<void> {
	await knex.schema.dropTable("products")
}
```
- Agora para executar essa **migration**, usamos o comando:
```zsh
npm run knex -- migrate:latest
```
