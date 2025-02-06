___
- Antes de fazer a primeira *migration*, precisamos antes fazer umas configurações adicionais que são:
1. Na raiz do nosso projeto criar um arquivo com o nome: `knexfile.ts`
2. E dentro desse arquivo vamos fazer o seguinte:
```ts
// knexfile.ts

import { config } from './src/database'

export default config
```
3. Voltamos ao arquivo `database.ts`e fazemos uma alteração também:
```ts
// database.ts

import { knex as setupKnex } from 'knex'

export const config = {
	client: 'sqlite',
	connection: {
		filename: './tmp/app.db'
	},
	useNullAsDefault: true,
}

export const knex = setupKnex(config)
```
4. Agora vamos no arquivo `package.json`e em *scripts* adicionamos o seguinte *script*:
```json
"knex": "node --import tsx ./node_modules/.bin/knex",
```
5. E agora usamos o `knex`da seguinte maneira:
```zsh
npm run knex -- -h
```
- Ele deve retornar todos os comandos que podemos usar utilizando o `knex`
6. Agora para criar uma `migration`, podemos usar o comando:
```zsh
npm run knex -- migrate:make nome-migration
```
- Ao rodar o comando ele irá criar uma pasta e um arquivo, esse arquivo é onde vamos criar a nossas tabelas e outras coisas do banco de dados;
7. Agora voltamos ao arquivo `database.ts`e precisamos fazer mais umas configurações para as `migrations`:
```ts
// database.ts

import { knex as setupKnex, Knex} from 'knex'

export const config: Knex.Config = {
	client: 'sqlite',
	connection: {
		filename: './db/app.db',
	},
	useNullAsDefault: true,
	migrations: {
		extension: 'ts',
		directory: './db/migrations',
	}	
}
```