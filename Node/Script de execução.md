___
- Para melhorar a experiencia de uso com o knex, vamos criar um script de execução para melhorar o uso dele.
- Para isso vamos seguir os passos abaixo:
1. No arquivo `package.json`, na parte de `scripts`, vamos criar o seguinte código:
```json
"knex": "node --import tsx ./node_modules/.bin/knex"
```
2. Agora para usar os comandos do knex, no terminal usamos da seguinte maneira:
```sh
npm run knex --
```
- `--` -> Indica pro npm que todos os argumentos que vamos passar em seguida devem ser passados diretamente para o comando que estamos executando;
3. Deixando então o nosso comando para `migrations`, da seguinte maneira:
```sh
npm run knex -- migrate:make nome-tabela
```