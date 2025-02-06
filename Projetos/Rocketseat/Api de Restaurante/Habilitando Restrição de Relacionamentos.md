___
- Vamos voltar ao arquivo de configuração do **Knex**, no caso o arquivo `knexfile.ts`e habilitar a restrição de chaves, para isso vamos alterar as configurações para:
```ts
export default {
	client: "sqlite3",
	connection: {
		filename: "./src/database/database.db",
	},
	pool: {
		afterCreate: (connection: any, done: any) => {
			connection.run("PRAGMA foreign_keys = ON")
			done()
		 }
	},
	useNullAsDefault: true,
	migrations: {
		extensions: "ts",
		directory: "./src/database/migrations"
	},
	seeds: {
		extensions: "ts",
		directory: "./src/database/seeds",
	}
}
```
- Essa configuração serve para o respeitar os relacionamentos entre as tabelas, para haver consistência em nosso banco de dados;