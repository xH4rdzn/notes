___
- Para listar todas as *migrations* que temos em nosso banco de dados usamos o comando abaixo:
```sh
npm run knex -- migrate:list
```
- E para desfazer uma *migration*, usamos o comando abaixo:
```sh
npm run knex -- migrate:down nomeDaMigration
```
- Na frente do `migrate:down`, informamos qual *migration* queremos desfazer
- O comando `migrate:down`, e para desfazermos uma *migration* especifica
- Outro comando que podemos utilizar é o `migrate:rollback`, esse comando vai voltar o último batch que você executou
```sh
npm run knex -- migrate:rollback
```
- Também podemos usar esse comando para desfazer todas as *migrations*, passando a flag `--all`
```sh
npm run knex -- migrate:rollback --all
```

