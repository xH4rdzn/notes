___
- Para validar nossas variáveis ambiente, vamos criar uma pasta chamada `env`, dentro da pasta `src`;
- E dentro da pasta `env`, vamos criar um arquivo `index.ts`;
- Agora vamos instalar a biblioteca do **Zod**, usamos o comando:
```zsh
npm i zod
```
- Agora voltando ao arquivo `index.ts`, vamos importar o **zod** e fazer como no exemplo a seguir:
```ts
import 'dotenv/config'
import { z } from 'zod'

const envSchema = z.object({
	NODE_ENV: z.enum(['development', 'test', 'production']).default('production')
	DATABASE_URL: z.string(),
	PORT: z.number().default(3333),
})

const _env = envSchema.safeParse(process.env)

if(_env.sucess === false) {
	console.error('Invalid environment variables!', _env.error.format())
	throw new Error('Invalid Environment variables!')
}

export const env = _env.data
```
- Agora para usarmos qualquer variável ambiente em vez de usarmos o `process.env`, usamos apenas `env`, que criamos 