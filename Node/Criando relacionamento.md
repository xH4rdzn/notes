___
- Antes vamos criar uma migration com o comando:
```sh
npm knex -- migrate:make create-course-modules
```
- Dentro da função `up`, vamos criar a tabela da seguinte maneira:
```ts
export async function up(knex: Knex): Promise<void> {
	await knex.schema.createTable("course_modules", (table) => {
		table.increments("id").primary(),
		table.text("name").notNullable(),

		// Criando relacionamento
		table.integer("course_id").notNullable().references("id").inTable("courses")
	})
}
```
- Lembrando que sempre que formos criar uma chave estrangeira, a chave estrangeira precisa ter o mesmo tipo de dado da chave primária na qual vamos referenciar;
- `integer()` -> recebe como parâmetro o nome da coluna;
- `references()` -> recebe como parâmetro o nome da coluna na qual vamos referenciar;
- `inTable()`-> recebe como parâmetro o nome da tabela que vamos relacionar;
