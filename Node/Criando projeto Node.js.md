___
- Vamos começar a estruturando o nosso projeto, para isso vamos iniciar o projeto com o comando:
```zsh
npm init -y
```
- Agora vamos criar uma pasta com o nome de `src`e dentro dessa pasta vamos criar o arquivo `server.ts`;
- E vamos instalar algumas coisas que vamos utilizar:
```zsh
npm i typescript @types/node tsx tsup -D
```
- Com as bibliotecas instaladas, vamos rodar o comando:
```zsh
npx tsc --init
```
- E no arquivo `tsconfig.json`, em *target*, alteramos para `ES2020`;
- Agora vamos instalar o `fastify`
```zsh
npm i fastify
```
- Voltamos a pasta `src`e vamos criar o arquivo `app.ts`. No arquivo `app.ts`, vamos instanciar a nossa aplicação:
```ts
import fastify from 'fastify'

export const app = fastify()
```
- E agora dentro do arquivo `server.ts`, vamos iniciar o nosso servidor:
```ts
import { app } from './app'

app.listen({
	host: '0.0.0.0',
	port: 3333,
}).then(() => {
	console.log('HTTP Server Running!')
})
```
- E na raiz do nosso projeto vamos criar o arquivo `.gitignore`
```.gitignore
node_modules
build
```
- Agora no arquivo `package.json`, vamos criar os `scripts`
```json
"scripts": {
	"start:dev": "tsx watch src/server.ts",
	"start": "node build/server.js"
	"build": "tsup src --out-dir build",
}
```