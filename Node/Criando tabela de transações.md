___
- Ao criarmos uma `migration`, percebemos que no arquivo criado ele vai ter dois métodos;
- O método `up`, é o método que diz o que essa `migration`vai fazer, como por exemplo criar uma tabela;
- O método `down`, ele tem que desfazer tudo que o método `up`, faz para caso de eventuais erros, é como se fosse um backup;
- Então para um arquivo de `migration`, vai seguir como no exemplo abaixo:
```ts
import type { Knex } from 'knex'

export async function up(knex: Knex): Promise<void> {
	await knex.schema.createTable('transactions', (table) => {
		table.uuid('id').primary()
		table.text('title').notNullable()
		table.decimal('amount', 10, 2).notNUllable()
table.timestamp('created_at').defaultTo(knex.fn.now()).notNullable()
	})
}

  
export async function down(knex: Knex): Promise<void> {
	await knex.schema.dropTable('transactions')
}
```
- Agora precisamos executar essa `migration`, para que ela entre no banco de dados, para isso usamos o comando:
```zsh
npm run knex -- migrate:latest
```
- Desta maneira já deve ter entrado a tabela criada no banco de dados
- Caso tenha faltado algum campo ou errado alguma coisa, e não enviamos para o nosso time, podemos executar o comando abaixo, para desfazer a `migration`:
```zsh
npm run kex -- migrate:rollback
```
- Para adicionar um novo campo a uma tabela já criada podemos gerar uma nova `migration`e fazer da seguinte maneira:
```ts
import type { Knex } from 'knex'

export async function up(knex: Knex): Promise<void> {
	await knex.schema.alterTable('transactions', (table) => {
		table.uuid('session_id').after('id').index()
	})
}


export async function down(knex: Knex): Promise<void> {
	await knex.schema.alterTable('transactions', (table) => {
		table.dropColumn('session_id')
	})
}
```