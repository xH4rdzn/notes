___
- Para começar na raiz do nosso projeto precisamos criar um arquivo com o nome de: `docker-compose.yml`;
- Dentro desse arquivo vamos fazer o seguinte:
```yml
services:
	service-pg:
		image: bitnami/postgresql
		ports:
			- '5432:5432'
		environment:
			- POSTGRES_USER=docker
			- POSTGRES_PASSWORD=docker
			- POSTGRES_DB=connect

	service-redis:
		image: bitnami/redis
		ports:
			- '6379:6379'
		environment:
			- ALLOW_EMPTY_PASSWORD=yes
```
- Agora para subir esses `containers` usamos o comando:
```zsh
docker compose up -d
```
- Agora voltamos ao arquivo `.env`e fazemos as seguintes alterações:
```env
PORT=3333

# Database

POSTGRES_URL="postgresql://docker:docker@localhost:5432/connect"
REDIS_URL="redis://localhost:6379"
```
- Agora voltamos ao `env.ts`e mudamos para:
```ts
import { z } from 'zod'

const envSchema = z.object({
	PORT: z.coerce.number().default(3333),
	POSTGRES_URL: z.string().url(),
	REDIS_URL: z.string().url()
})

export const env = envSchema.parse(process.env)
```
- Agora para criar a conexão com `redis`, dentro da pasta `src`vamos criar a pasta `redis`e dentro dessa pasta vamos criar o arquivo `client.ts`
- E agora instalamos a biblioteca:
```zsh
npm i ioredis
```
- Agora dentro do arquivo `client.ts`, vamos fazer as seguintes configurações:
```ts
import { Redis } from 'ioredis'
import { env } from '../env'

export const redis = new Redis(env.REDIS_URL)
```
- Desta maneira a nossa conexão com o *redis* já está pronta;
- Agora para fazer a conexão com *postgresql*, dentro da pasta `src`, vamos criar uma pasta com o nome `drizzle`, dentro dessa pasta vamos criar um arquivo com o nome `client.ts`, e agora vamos instalar duas bibliotecas, com o seguinte comando:
```zsh
npm i postgres drizzle-orm
```
- E também vamos precisar instalar a seguinte biblioteca:
```zsh
npm i drizzle-kit -D
```
- Voltamos ao arquivo `Client.ts`que criamos dentro da pasta `drizzle`e fazemos o seguinte:
```ts
import postgres from 'postgres'
import { drizzle } from 'drizzle-orm/postgres-js'
import { env } from '../env'

export const pg = postgres(env.POSTGRES_URL)
export const db = drizzle(pg)
```
- E agora dentro da pasta `drizzle`, vamos criar a pasta `schema`, que é onde vamos criar as tabelas do nosso banco de dados *postgres*;
- Dentro dessa pasta vamos criar um arquivo para cada tabela, neste caso vamos criar a tabela `subscriptions.ts`;
```ts
import { pgTable, uuid } from "drizzle-orm/pg-core"

export const subscriptions = pgTable('subscriptions', {
	id: uuid('id').primaryKey().defaultRandom(),
	name: text('name').notNull(),
	email: text('email').notNull().unique(),
	createdAt: timestamp('created_at').notNull().defaultNow(),
})
```
- Agora voltamos ao arquivo `client.ts`que está dentro da pasta `drizzle`e fazemos as seguintes alterações:
```Ts
import postgres from 'postgres'
import { drizzle } from 'drizzle-orm/postgres-js'
import { env } from '../env'

export const pg = postgres(env.POSTGRES_URL)
export const db = drizzle(pg, {
	schema: {
		subscriptions,
	}
})
```
- Agora na raiz do nosso projeto vamos criar um arquivo com o nome de `drizzle.config.ts` e dentro desse arquivo vamos fazer:
```Ts
import type { Config } from 'drizzle-kit'

export default {
	schema: './src/drizzle/schema/*',
	out: './src/drizzle/migrations',
	dialect: 'postgresql',
	dbCrendentials: {
		url: env.POSTGRES_URL	
	},
} satisfies Config
```
- E agora no terminal rodamos o comando:
```zsh
npx drizzle-kit generate
```
- Ele vai apenas criar o arquivo `SQL` da nossa tabela, agora para executar essa migration em nosso banco de dados precisamos executar o comando:
```zsh
npx drizzle-kit migrate
```
- Desta maneira ele executa a migration em nosso banco de dados;
- 