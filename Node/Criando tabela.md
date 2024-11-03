___
- Após executar o [[Script de execução|ultimo comando]], será gerado um arquivo `Typescript`.
- Dentro desse arquivo `Typescript`, vai ser gerado um código com duas funções: `up` e `down`
- A função `up`, é responsável por enviar as alterações para o banco de dados
- A função `down`, é para desfazer o que uma migration fez.
- Então agora para criarmos uma tabela, seguimos o exemplo abaixo:
```ts
export async function up(knex: Knex): Promise<void> {
	await knex.schema.createTable("courses", (table) => {
	})
}
```
- O primeiro parâmetro do método `createTable`, é o nome que queremos dar a nossa tabela
- O segundo parâmetro é uma função que recebe como parâmetro o `table`, e dentro dessa função usamos o `table`, para criar as colunas. Como segue no exemplo abaixo:
```ts
export async function up(knex: Knex): Promise<void> {
	await knex.schema.createTable("courses", (table) => {
		table.increments("id").primary(),
		table.text("name").notNullable()
	})
}
```
- `increments()` -> Recebe como parâmetro o nome da tabela, e define que essa coluna é do tipo `AUTOINCREMENT`;
- `primary()` -> Define a chave primária;
- `text()` -> Recebe como parâmetro o nome da tabela, e define que essa coluna é do tipo `TEXT`;
- `notNullable()` -> equivale ao `NOT NULL` do SQL;
- `timestamp()` -> Recebe como argumento o nome da tabela, e define que a coluna é do tipo `Date/time`, normalmente usamos com o comando `defaultTo`, que recebe como parâmetro funções padrões do `Knex`, que usamos da seguinte maneira:
```ts
table.timestamp("created_at").defaultTo(knex.fn.now())
```
- `now()` -> retorna a data e o horário atual;

- Dentro da função `down`, precisamos fazer a operação inversa da função `up`, nesse exemplo, como criamos uma tabela, no `down`, precisamos passar o código para poder remover essa tabela do banco de dados. Ficando da seguinte maneira:
```ts
export async function down(knex: Knex): Promise<void> {
	await knex.schema.dropTable("courses")
}
```
- `dropTable` -> Apagar uma tabela;
- Agora para aplicar essa `migration`, no terminal usamos o seguinte comando:
```sh
npm run knex -- migrate:latest
```