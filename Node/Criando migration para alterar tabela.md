___
- Para criar uma nova migration usamos o comando abaixo:
```sh
npm run knex -- migrate:make add-updated-courses
```
- `migrate:make` -> para criar uma nova migration com o knex;
- E agora no arquivo gerado, vamos na função `up` e usamos da seguinte maneira para poder alterar uma tabela:
```ts
export async function up(knex: Knex): Promise<void> {
	await knex.schema.alterTable("courses", (table) => {
		table.timestamp("updated_at").defaultTo(knex.fn.now()).after("created_at")
	})
}
```
- `alterTable()` -> Usamos esse comando para alterar a tabela, como *primeiro parâmetro*, informamos a tabela que vamos alterar, como *segundo parâmetro*, passamos uma arrow function,como no exemplo acima.
- `knex.fn.now()` -> Função do `knex`, para pegar a data e a hora;
- `after()` -> podemos colocar na ordem, nesse caso informamos que esse campo vai ficar depois do campo que passarmos como parâmetro para o `after`
- Como na função `down`, fazemos a operação contrária do `up`, o nosso código vai ficar da seguinte maneira:
```ts
export async function down(knex: Knex): Promise<void> {
	await knex.schema.alterTable("courses", (table) => {
		table.dropColumn("updated_at")
	})
}
```
- Agora para executar essa migration usamos o comando abaixo:
```sh
npm run knex -- migrate:latest
```