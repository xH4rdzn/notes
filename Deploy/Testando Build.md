___
- Para testarmos o nosso *build*, como está em `Javascript`puro podemos rodar ele com o *NODE*, para isso podemos usar o comando abaixo:
```zsh
node build/server.js
```
- Porém vai dar erro de validação por conta das variáveis ambiente, para poder usar o arquivo `.env`, precisamos usar o comando da seguinte maneira:
```zsh
node --env-file=.env build/server.js
```
- Desta maneira a nossa aplicação deve funcionar, mas em vez de ficarmos digitando esse comando toda vez, vamos criar um `script`no arquivo `package.json`
```json
"start": "node --env-file=.env build/server.js"
```
- E agora podemos usar ele da seguinte maneira:
```zsh
npm run start
```
- Ou podemos usar:
```zsh
npm start
```
- Após testarmos podemos alterar o `script`para:
```json
"start": "node build/server.js"
```
- Pois vamos criar o arquivo de variáveis ambiente dentro do nosso `deploy`