___
- Após fazer [instalação do knex](./Instalando%20o%20Knex.js.md), precisamos fazer a configuração dele. Então vamos seguir os passos abaixo:
1. Na raiz do nosso projeto criamos um arquivo com o nome de: `knexfile.ts`
2. Dentro desse arquivo, vamos escrever o seguinte código:
```ts
export default {
	client: "sqlite3", // Aqui depende do Driver
	connection: {
		filename: ""
	}
}
```
3. Agora dentro da pasta `src`, criamos uma nova pasta com o nome de `database`
- Essa pasta vai ser onde vai ficar o nosso banco de dados `sqlite`
4. Agora informamos o caminho para o `filename`, que está no arquivo do `knexfile.ts`
```ts
export default {
	client: "sqlite3", // Aqui depende do Driver
	connection: {
		filename: "./src/database/database.db"
	},
	useNullAsDefault: true,
	migrations: {
		extensions: "ts",
		directory: "./src/database/migrations"
	}
}
```
5. Pronto, já temos o `knex` configurado para fazer o uso em nossa aplicação.