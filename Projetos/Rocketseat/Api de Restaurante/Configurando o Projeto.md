___
- Vamos instalar o `express`
```zsh
npm i express
```
- Agora vamos instalar o `typescript`
```zsh
npm i typescript @types/node -D
```
- Agora na raiz do nosso projeto vamos criar a pasta `src` e dentro dessa pasta vamos criar o arquivo `server.ts`
- Também na raiz podemos criar o arquivo `tsconfig.json`, e colocamos as seguintes configurações:
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
- Agora voltamos ao arquivo `server.ts`, e importamos o express:
```ts
import express from "express"
```
- Porém ele vai pedir para instalar as tipagens do `express`, para isso usamos o comando:
```zsh
npm i --save-dev @types/express
```
- Então continuamos no arquivo `server.ts`
```ts
import express from "express"

const PORT = 3333
const app = express()
app.use(express.json())

app.listen(PORT, () => console.log(`Server is running on port ${PORT}`))
```
- Agora voltamos ao arquivo `package.json`, e vamos adicionar um script para executar o nosso servidor, porém para isso precisamos da biblioteca `tsx`, então instalamos ela com o comando:
```zsh
npm i tsx -D
```
- E então no arquivo `package.json`, criamos o script:
```json
"dev": "tsx watch src/server.ts"
```
- Agora para executarmos o nosso servidor, no terminal usamos o comando:
```zsh
npm run dev
```
