___
- Para criarmos o projeto, primeiro vamos navegar até a pasta desejada e vamos fazer o seguinte:
```zsh
mkdir desafioFullStackComIa
```
- Vamos entrar nessa pasta
```zsh
cd desafioFullStackComIa
```
- E agora vamos iniciar o nosso projeto com ***`pnpm`*** com o comando:
```zsh
pnpm init
```
- Agora podemos abrir em nossa IDE
____
### Criando apenas um repositório
- Em nosso arquivo ***`package.json`***, vamos retirar algumas linhas e deixar da seguinte maneira:
```json
{
	"name": "WebhookInspector",
	"version": "1.0.0",
	"description": "",
	"private": true,
	"workspaces": [
		"api",
		"web"
	],
	"packageManager": "pnpm@10.20.0"
}
```
- Agora vamos criar o arquivo ***`pnpm-workspace.yaml`*** e dentro dele vamos fazer o seguinte:
```yaml
packages:
	- 'api'
	- 'web'  
```
- Agora podemos criar a pasta `api` e depois utilizando o comando abaixo vamos criar o `web`
```zsh
pnpm create vite@latest web
```
- Nas opções vamos escolher: 
	- React
	- Typescript 
- Agora vamos apagar alguns arquivos que estão na pasta web:
	- `README.MD`
	- `eslint.config.js`
	- No arquivo `index.html`, vamos remover a importação do svg
	- `App.css`
	- Arrumamos as importações e removemos as dependências do `eslint`, entramos na pasta e instalamos novamente as dependências;
___
### Configurando Back-end
- Acessamos a pasta `api`, via terminal e iniciamos o projeto com o comando:
```zsh
pnpm init
```
- Dentro da pasta `api`, vamos criar a pasta `src`, e agora vamos instalar umas dependências que vamos utilizar para desenvolvimento, usando o comando:
```zsh
pnpm i typescript @types/node tsx -D
```
- E agora vamos configurar o typescript, para isso usamos o comando:
```zsh
pnpm tsc --init
```
- Dentro do arquivo `tsconfig.json`, vamos colocar as seguintes configurações:
```json
{
	"$schema": "https://json.schemastore.org/tsconfig",
	"_version": "24.0.0",
	"compilerOptions": {
		"lib": [
			"es2024",
			"ESNext.Array",
			"ESNext.Collection",
			"ESNext.Iterator",
			"ESNext.Promise"
		],
		"module": "nodenext",
		"target": "es2024",
		"strict": true,
		"esModuleInterop": true,
		"skipLibCheck": true,
		"moduleResolution": "node16",
		"paths": {
			"@/*": [
				"./src/*"
			]
		}
	}
}
```
- Agora no arquivo ***`package.json`***, vamos criar um *script* para podermos rodar o nosso servidor
```json
"dev": "tsx watch src/server.ts"
```
- E agora vamos instalar o ***`fastify`***, usando o comando:
```zsh
pnpm i fastify
```
- E dentro do arquivo `server.ts`, vamos fazer o seguinte:
```ts
import { fastify } from 'fastify'

const app = fastify()

app.listen({ port: 3333, host: '0.0.0.0' }).then(() => {
	console.log('HTTP server running!')
})
```
- Agora na raiz da nossa `api`, vamos criar o arquivo `.env`, com esse arquivo precisamos mudar o nosso script `dev`, para:
```json
"dev": "tsx watch --env-file=.env src/server.ts",
"start": "node dist/server.js"
```
___
### Configurando o *Biome*
- Para instalarmos o ***`Biome`***, vamos usar o comando:
```zsh
pnpm add -D -E @biomejs/biome
```
- Agora para iniciar a sua configuração vamos usar o comando:
```zsh
pnpm exec biome init
```
- No arquivo `biome.json`, que irá ser criado podemos configurar como ele deve fazer o *linting* do nosso código
- Feito isso, o *Biome* já esta configurado, e podemos fazer um script:
```json
"format": "biome format --write"
```
____
### Configurando o Swagger com Scalar
- Agora vamos configurar o nosso servidor, para isso vamos instalar as seguintes bibliotecas:
```zsh
pnpm i @fastify/cors @fastify/swagger zod fastify-type-provider-zod @scalar/fastify-api-reference
```
- Agora no arquivo `server.ts`, vamos adicionar as seguintes importações:
```ts
import { serializerCompiler, validatorCompiler, jsonSchemaTransform, type ZodTypeProvider } from 'fastify-type-provider-zod'
import { fastifySwagger } from '@fastify/swagger'
import { fastifyCors } from '@fastify/cors'
import ScalarApiReference from '@scalar/fastify-api-reference'
```
- E agora registramos essas ferramentas no nosso servidor:
```ts
import { fastify } from 'fastify'
import {
	serializerCompiler,
	validatorCompiler,
	jsonSchemaTransform,
	type ZodTypeProvider,
} from 'fastify-type-provider-zod'
import { fastifySwagger } from '@fastify/swagger'
import { fastifyCors } from '@fastify/cors'
import ScalarApiReference from '@scalar/fastify-api-reference'

  
const app = fastify().withTypeProvider<ZodTypeProvider>()

  

app.setValidatorCompiler(validatorCompiler)
app.setSerializerCompiler(serializerCompiler)

  

app.register(fastifyCors, {
	origin: true,
	methods: ['GET', 'PUT', 'POST', 'PATCH', 'DELETE', 'OPTIONS'],
})

  

app.register(fastifySwagger, {
	openapi: {
		info: {
			title: 'WebHook Inspector API',
			description: 'API for capturing and inspecting webhook requests',
			version: '1.0.0',
		},
	},
	transform: jsonSchemaTransform,
})

  

app.register(ScalarApiReference, {
	routePrefix: '/docs',
})

  

app.listen({ port: 3333, host: '0.0.0.0' }).then(() => {

console.log('HTTP Server running on http://localhost:3333')
console.log('Docs avaliable on http://localhost:3333/docs')
})
```
- Agora podemos criar as nossas rotas, para isso dentro de `src`, vamos criar a pasta `routes`e dentro dela vamos criar cada arquivo para uma rota, como no exemplo abaixo:
```ts
export const listWebhooks: FastifyPluginAsyncZod = async (app) => {
	app.get(
	'/api/webhooks',
	{
		schema: {
			summary: 'List webhooks',
			tags: ['Webhooks'],
			querystring: z.object({
				limit: z.coerce.number().min(1).max(100).default(20),
			}),
			response: {
				200: z.array(
					z.object({
						id: z.string(),
						method: z.string(),
					})
				)
			},
		},
	},
	async (request, reply) => {
		// código a ser executado na rota
	}
	)
}
```
- Voltamos ao arquivo `server.ts`e registramos a nossa rota
```ts
app.register(listWebhooks)
```
- Agora vamos tipar as nossas variáveis ambiente, para isso vamos criar um arquivo `env.ts`e dentro dele vamos fazer o seguinte:
```ts
import { z } from 'zod'

const envSchema = z.object({
	NODE_ENV: z.enum(['development', 'production', 'test']).default('development'),
	PORT: z.coerce.number().default(3333),
	// Outras variáveis ambiente
})

export const env = envSchema.parse(process.env)
```
____
### Configurando Banco de dados
- Para configurar o nosso banco de dados, na raiz do nosso projeto, vamos criar o arquivo ***`docker-compose.yml`***
- E dentro dele vamos fazer as seguintes configurações:
```yml
services:
	postgres:
		image: postgres:17
		container_name: webhooks_db
		environment:
			POSTGRES_USER: docker
			POSTGRES_PASSWORD: docker
			POSTGRES_DB: webhooks
		ports:
			- '5432:5432'	
```
- E agora podemos usar o comando, para subir o nosso banco de dados:
```zsh
docker compose up -d 
```
- E agora no arquivo `.env`, vamos configurar a nossa conexão com o banco de dados:
```env
DATABASE_URL="postgresql://docker:docker@localhost:5432/webhooks
```
- Voltamos ao arquivo `env.ts`e adicionamos o `DATABASE_URL`;
____
### Configurando o drizzle
- Vamos começar instalando ele com o comando:
```zsh
pnpm i drizzle-kit -D
```
- E também vamos instalar:
```zsh
pnpm i drizzle-orm drizzle-zod pg
```
- E depois vamos instalar:
```zsh
pnpm i @types/pg -D
```
- Agora na raiz do nosso projeto, vamos criar o arquivo ***`drizzle.config.ts`*** e dentro dele vamos fazer o seguinte:
```ts
import { defineConfig } from 'drizzle-kit'

export default defineConfig({
	dialect: 'postgresql',
	dbCredentials: {
		url: env.DATABASE_URL,
	},
	out: './src/db/migrations',
	schema: './src/db/schema/index.ts',
	casing: 'snake_case',
})
```
- Agora na pasta `src`, vamos criar uma pasta `db`e dentro dela vamos criar duas pastas (`migrations`e `schema`) e um arquivo `index.ts`
- Agora nesse arquivo `index.ts`, vamos fazer as seguintes configurações:
```ts
import { drizzle } from 'drizzle-rm/node-postgres'
import { env } from '@/env'

export const db = drizzle(env.DATABASE_URL, {
	casing: 'snake_case',
})
```
- Agora dentro da pasta `schema`, vamos criar o arquivo `webhooks.ts`, esse arquivo vai ser a definição da nossa tabela
```ts
export const webhooks = pgTable('webhooks', {
	id: text().primaryKey().$defaultFn(() => uuidv7()),
	method: text().notNull(),
	pathname: text().notNull(),
	ip: text().notNull(),
	statusCode: integer().notNull().default(200),
	contentType: text(),
	contentLength: integer(),
	queryParams: jsonb().$type<Record<string,string>>(),
	headers: jsonb().$type<Record<string,string>>().notNull(),
	body: text(),
	createdAt: timestamp().notNull().defaultNow(),
})
```
- Precisamos instalar o pacote abaixo:
```zsh
pnpm i uuidv7
```
- Agora no arquivo `index.ts`dentro da pasta `schema`fazemos o seguinte:
```ts
export * from './webhooks'
```
- E no arquivo `index.ts`que está na pasta `db` adicionamos esse arquivo da seguinte maneira:
```ts
import { drizzle } from 'drizzle-rm/node-postgres'
import { env } from '@/env'
import * as schema from './schema'

export const db = drizzle(env.DATABASE_URL, {
	schema,
	casing: 'snake_case',
})
```
- Agora vamos no nosso arquivo ***`package.json`*** e vamos criar 3 scripts:
```json
"db:generate": "drizzle-kit generate",
"db:migrate": "drizzle-kit migrate",
"db:studio": "drizzle-kit studio"
```
- O comando `generate`, lê o arquivo do `schema`e cria o sql necessário;
- O comando `migrate`, executa as migrations no nosso banco de dados
- O comando `studio`, ele cria uma URL na qual podemos ver o nosso banco de dados.