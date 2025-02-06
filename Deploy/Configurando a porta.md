___
- Como não mandamos o arquivo `.env`, para o git, se baixarmos o projeto, normalmente o projeto deve ter um `.env-example`, para dizer quais variáveis de ambiente vamos utilizar no projeto.
- Fazemos isso para não deixar de maneira *pública* variáveis sensíveis do projeto.
- Vamos configurar a porta, para caso precisamos mudar, só alteramos nas variáveis de ambiente.
- Para isso vamos no arquivo `env.ts`e como estamos o zod vamos mudar para:
```ts
import { z } from "zod"

const envSchema = z.object({
	DATABASE_URL: z.string().url(),
	JWT_SECRET: z.string(),
	PORT: z.coerce.number().default(3333)
})

export const env = envSchema.parse(process.env)
```
- Usamos o método `coerce`, para garantir que o dado esteja no formato que desejamos. Nesta caso um número.