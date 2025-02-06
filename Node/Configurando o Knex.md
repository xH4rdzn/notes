___
- Podemos acessar a documentação oficial do [Knex.js](https://knexjs.org/);
- Para fazer a instalação do *knex*, usamos o comando abaixo:
```zsh
npm i knex
```
- Além dele precisamos também instalar o driver nativo do banco de dados que vamos utilizar, nesse caso vamos usar o `sqlite`então usamos o comando abaixo:
```zsh
npm i sqlite3
```
- Agora dentro da pasta `src`, criamos o arquivo `database.ts`, esse arquivo vai conter as configurações de conexão com o banco de dados:
```ts
// database.ts

import { knex as setupKnex } from 'knex'

export const knex = setupKnex({
	client: 'sqlite',
	connection: {
		filename: './tmp/app.db'
	},
	useNullAsDefault: true,
})
```
- Após isso inicialmente já esta configurada a conexão com o banco de dados, para podemos testar se deu tudo certo podemos criar uma rota teste e fazer da seguinte maneira:
	- Não podemos esquecer de fazer a importação do `knex`do arquivo `database.ts`que criamos;
```ts
app.get('/hello', async () => {
	const tables = await knex('sqlite_schema').select('*')

	return tables
})
```
- Ao testarmos, se der tudo certo deve retornar um `array`vazio;