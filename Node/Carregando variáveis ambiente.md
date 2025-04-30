___
- Na raiz do nosso projeto vamos criar o arquivo `.env`e dentro desse arquivo vamos colocar:
```.env
NODE_ENV=dev
```
- E criamos outro arquivo com o nome de `.env_example`, e colocamos o `.env`no arquivo `.gitignore`;
- Para carregar essas variáveis agora precisamos instalar a `dotenv`com o comando:
```zsh
npm i dotenv
```
- Agora dentro da pasta `src`, vamos criar a pasta `env`e dentro dessa pasta vamos criar um arquivo `index.ts`
- E também vamos instalar o `zod`, com o comando:
```zsh
npm i zod
```
- E agora dentro do arquivo `index.ts`, vamos fazer o seguinte:
```ts
import 'dotenv/config'
import { z } from 'zod'

const envSchema = z.object({
	NODE_ENV: z.enum(['dev', 'test', 'production']).default('dev'),
	PORT: z.coerce.number().default(3333),
})

const _env = envSchema.safeParse(process.env)

if(_env.sucess === false) {
	console.error('Variáveis ambiente inválidas', _env.error.format())
	throw new Error('Variáveis ambiente inválidas')
}

export const env = _env.data
```
- E agora para testar, voltamos ao arquivo `server.ts`e fazemos o uso da seguinte maneira:
```ts
import { app } from './app'
import { env } from './env'

app.listen({
	host: '0.0.0.0',
	port: env.PORT,
}).then(() => {
	console.log('HTTP Server Running!')
})
```
- E rodamos o script para iniciar o servidor, para ver se está tudo certo.