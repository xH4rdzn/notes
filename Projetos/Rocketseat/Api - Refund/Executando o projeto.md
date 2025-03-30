___
- Agora que [[Projetos/Rocketseat/Api - Refund/Criando o projeto|criamos o projeto]], na raiz do nosso projeto, podemos criar pasta `src`;
- Dentro dessa pasta podemos criar o arquivo `app.ts`, e fazemos o seguinte nesse arquivo:
```ts
import express from "express"

const app = express()
app.use(express.json())

export { app }
```
- E agora ainda dentro da pasta `src`, vamos criar o arquivo `server.ts`e dentro dele fazemos o seguinte:
```ts
import { app } from './app'
```
- E também podemos fazer a configuração do `TypeScript`, para isso na raiz do nosso projeto criamos o arquivo `tsconfig.json`e dentro dele fazemos a seguinte configuração:
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
- Agora voltamos ao arquivo `server.ts`e adicionamos e fazemos a seguinte alteração:
```ts
import { app } from '@/app'

const PORT = 3333

app.listen(PORT, () => console.log(`Server is running on port ${PORT}`))
```
- Agora voltamos ao arquivo `package.json`e vamos criar um novo script, para poder fazer a execução do nosso servidor:
```json
"dev": "tsx watch src/server.ts"
```
- E agora podemos executar o nosso projeto com o comando:
```zsh
npm run dev
```