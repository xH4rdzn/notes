___
- Para instalar o `Knex.js`, vamos usar o comando:
```zsh
npm i knex
```
- E como vamos utilizar o `sqlite`precisamos instalar ele também, usando o comando:
```zsh
npm i sqlite3
```
- Agora na raiz do nosso projeto, criamos o arquivo `knexfile.ts` e nesse arquivo vamos por as configurações abaixo:
```ts
export default {
	client: "sqlite3",
	connection: {
		filename: "./src/database/database.db",
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
- Agora vamos na pasta `src`e dentro dela criamos a pasta `database`
![[Pasted image 20250204171930.png]]
- Após isso vamos no arquivo `package.json`e vamos adicionar o seguinte *script*
```json
"knex": "node --import tsx ./node_modules/.bin/knex"
```
- Agora para criar a nossa primeira **migration**, usamos o comando:
```zsh
npm run knex -- migrate:make create-products
```
- Dentro da pasta `database`, deve ser gerado a pasta `migrations`e o arquivo da `migration`;