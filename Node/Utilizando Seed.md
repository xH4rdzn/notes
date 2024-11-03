___
- Existem cenários que precisamos popular uma tabela do nosso banco de dados com vários dados;
- Para fazer isso podemos usar um recurso do Query Builder que chamamos de `seed`, que podemos popular com vários registro de uma só vez;
- Para fazermos isso, utilizando o `knex`, vamos fazer da seguinte maneira:
1. Voltamos ao arquivo `knexfile.ts` e adicionamos o seguinte código:
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
	},
	seeds: {
		extensions: "ts",
		directory: "./src/database/seeds",
	},
}
```
2. Agora para criar o nosso `seed`, usamos o comando abaixo:
```sh
npm run knex -- seed:make insert-courses
```
3. Irá ser gerado um arquivo com o nome que passamos no comando acima, basta preencher o arquivo nos locais necessários
4. Agora para executar o nosso `seed`, usamos o comando abaixo:
```sh
npm run knex -- seed:run
```
