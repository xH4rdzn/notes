___
- Usamos o `seed`, para popular uma tabela no banco de dados, com múltiplos dados em uma única vez
- Para criar um `seed`com o knex, usamos o comando:
```zsh
npm run knex -- seed:make insert-products
```
- No arquivo gerado, podemos apagar os comentários
- Na primeira linha, mudamos para o nome da nossa tabela na qualquer queremos inserir esses dados, para que ele limpe a tabela.
- Após inserir os dados desejados, usamos o comando:
```zsh
npm run knex -- seed:run
```
- Para poder executar todos os `seeds`, da nossa aplicação.