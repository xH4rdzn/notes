___
- A ferramenta de Query Builder que vamos utilizar é o [Knex.js](https://knexjs.org/guide/query-builder.html);
- Para instalar ele em nossa aplicação usamos o comando:
```sh
npm i knex
```
- Precisamos também instalar o driver do banco de dados que vamos utilizar, nesse caso vamos usar o `SQLite`, então instalamos ele com o comando abaixo:
```sh
npm i sqlite3
```
- Após a instalação do `Knex` e do driver do banco de dados já podemos utilizar ele em nossa aplicação.
- *Podemos usar qualquer outro banco de dados suportado pelo Knex, só precisamos olhar na documentação oficial*;