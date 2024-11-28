___
- Criamos uma pasta para o nosso projeto, neste caso vai ser o `rocketlog`
```zsh
mkdir rocketlog
```
- Agora podemos acessar essa pasta
```zsh
cd rocketlog
```
- Acessando a pasta, abrimos ela no *VSCode*
```zsh
code .
```
- Abrindo essa pasta no *VSCode*, podemos iniciar o nosso projeto node:
```zsh
npm init -y
```
- Após iniciarmos o projeto node, podemos instalar o `express`
```zsh
npm i express
```
- Devemos também instalar a tipagem do `express`
```zsh
npm i --save-dev @types/express
```
- Agora na raiz do nosso projeto, podemos criar a pasta `src`, que vai ser onde vai ficar todo o código fonte da nossa aplicação
- Ao criar a pasta `src`, criamos dois arquivos o `app.ts` e o `server.ts`
- No arquivo `app.ts`, vamos escrever o seguinte código:
```ts
// Arquivo app.ts
import express from "express"

const app = express()
app.use(express.json())

export { app }
```
- No arquivo `server.ts`, vamos escrever o seguinte código:
```ts
// Arquivo server.ts
import { app } from "./app"

const PORT = 3333

app.listen(PORT, () => console.log(`Server is Running on port ${PORT}`))
```
- Agora vamos instalar o `typescript`, com o comando:
```zsh
npm i typescript -D
```
- E também as tipagens do node:
```zsh
npm i @types/node -D
```
- Vamos precisar também do `tsx`, instalamos com o comando:
```zsh
npm i tsx -D
```
- E agora vamos configurar o nosso `typescript`, para isso usamos o comando abaixo:
```zsh
npx tsc --init
```
- No arquivo `tsconfig.json`, por as seguintes configurações:
```json
{
	"compilerOptions": {
		"target": "ES2022",
		"lib": ["ES2023"],
		"paths": {
			"@/*": ["./src/*"]
		},
		"module": "Node16",
		"esModuleInterop": true,
		"forceConsistentCasingInFileNames": true,
		"strict": true,
		"skipLibCheck": true
	}
}
```
- Agora dentro do arquivo `package.json`, podemos criar o nosso script:
```json
{
	"scripts": {
		"dev": "tsx watch src/server.ts"
	}
}
```
*Desta maneira a estrutura inicial do nosso projeto está pronta;