___
- Para iniciar o nosso projeto vamos usar o comando:
```zsh
npm init -y
```
- E agora vamos fazer a instalação do `fastify`
```zsh
npm i fastify
```
- Com o `fastify`instalado, podemos criar o nosso servidor, para isso, na raiz do nosso projeto vamos criar a pasta `src` e dentro dela vamos criar o arquivo `server.ts`;
- Agora vamos instalar o `tsx`, `typescript`e o pacote de tipagens para o node;
```zsh
npm i tsx typescript @types/node -D
```
- Após a instalação podemos iniciar a configuração do `typescript`, com o comando:
```zsh
npx tsc --init
```
- E pegamos as configurações do seguinte link [TsConfig](https://github.com/tsconfig/bases), de acordo com a versão do node que vamos utilizar, neste caso a *22*;
- E colamos as configurações dentro do arquivo `tsconfig.json`;
- Agora voltamos ao arquivo `server.ts`e testamos se está funcionando, caso esteja, vamos criar um `script`, no arquivo `package.json`
```json
"scripts": {
	"dev": "tsx watch src/server.ts"
},
```
- Agora dentro do arquivo `server.ts`, vamos criar o nosso servidor da seguinte maneira:
```ts
import { fastify } from "fastify"

const app = fastify()

app.listen({ port: 3333}).then(() => {
	console.log('HTTP Server Running!')
})
```
- Agora vamos instalar a biblioteca `fastify/cors`, para isso usamos o comando:
```zsh
npm i @fastify/cors
```
- `CORS`-> é uma medida de segurança, para definirmos quais `URL's`do nosso front-end vai poder acessar o nosso back-end, e o configuramos da seguinte maneira:
```ts
import { fastify } from "fastify"
import { fastifyCors } from "@fastify/cors"

const app = fastify()

app.register(fastifyCors, {
	origin: // URL do nosso front-end, em ambiente de produção
})

app.listen({ port: 3333}).then(() => {
	console.log('HTTP Server Running!')
})
```
- Para ambientes de desenvolvimento, podemos fazer da seguinte maneira:
```ts
import { fastify } from "fastify"
import { fastifyCors } from "@fastify/cors"

const app = fastify()

app.register(fastifyCors)

app.listen({ port: 3333}).then(() => {
	console.log('HTTP Server Running!')
})
```
- Agora vamos instalar o `zod`, para poder validar dados, para isso usamos o comando:
```zsh
npm i zod
```
- E também precisamos instalar a biblioteca que integra o `zod`, com o `fastify`, para isso usamos o comando:
```zsh
npm i fastify-type-provider-zod
```
- Agora usamos eles da seguinte maneira:
```ts
import { fastify } from "fastify"
import { fastifyCors } from "@fastify/cors"
import { validatorCompiler, serializerCompiler } from "fastify-type-provider-zod"

const app = fastify()

app.setSerializerCompiler(serializerCompiler)
app.setValidatorCompiler(validatorCompiler)

app.register(fastifyCors)

app.listen({ port: 3333}).then(() => {
	console.log('HTTP Server Running!')
})
```
- Agora nosso aplicativo faz validações de maneira automática, como no exemplo abaixo:
```ts
import { z } from 'zod'

app.post('/subscriptions', {
	schema: {
		body : z.object({
				name: z.string(),
				email: z.string().email()
			})
	},
} ,(request, reply) => {
	// Código aqui
})
```
- Usamos o `body`, quando temos o método `post`ou `putch`
- `Search Params (Query Params)`, são aqueles parâmetros que vem depois do `?`, e são opcionais
- Os `Routes Params`, são usamos para identificação de recursos
- Agora na `const app`, precisamos fazer a seguinte alteração, para as validações do `zod`funcionar
```Ts
const app = fastify().withTypeProvider<ZodTypeProvider>()
```
- Agora quando voltarmos na rotas que definimos o `schema`, ele identifica automaticamente o que temos no *corpo da requisição*;
- Agora para devolver uma reposta usamos o `reply`, como no exemplo abaixo:
```Ts
import { z } from 'zod'

app.post('/subscriptions', {
	schema: {
		body : z.object({
				name: z.string(),
				email: z.string().email()
			})
	},
} ,(request, reply) => {
	const { name, email } = request.body

	return reply.status(201).send({
		name,
		email,
	})
})
```
- E o `serializerCompiler`serve para devolvermos repostas de acordo com o `status code`dela, como no exemplo abaixo:
```Ts
import { z } from 'zod'

app.post('/subscriptions', {
	schema: {
		body : z.object({
				name: z.string(),
				email: z.string().email()
			}),
		response: {
			201: z.object({
				name: z.string(),
				email: z.string().email(),
			})
		}
	},
} , async (request, reply) => {
	const { name, email } = request.body

	return reply.status(201).send({
		name,
		email,
	})
})
```
- Agora vamos instalar uma biblioteca para poder documentar a nossa `api`, para isso usamos o comando:
```zsh
npm i @fastify/swagger @fastify/swagger-ui
```
- Agora importamos essa bibliotecas:
```ts
import { fastifySwagger } from "@fastify/swagger"
import { fastifySwaggerUi } from "@fastify/swagger-ui"
```
- Após a importação, qualquer lugar após a `const app`fazemos:
```ts
app.register(fastifySwagger, {
	openapi: {
		info: {
			title: 'NLW Connect',
			version: '0.0.1'
		},
	},
	transform: jsonSchemaTransform, // isso aqui é importado do fastify-type-provider-zod
})
```
- E agora vamos registrar o `fastifySwaggerUi`, como no exemplo abaixo:
```ts
app.register(fastifySwaggerUi, {
	routePrefix: '/docs',
})
```
- Porém esse plugin só reconhece quando as rotas estão separadas do arquivo do servidor, para isso dentro da pasta `src`, vamos criar a pasta `routes`e dentro dela vamos criar um arquivo para as rotas e dentro desse arquivo vamos fazer da seguinte maneira:
```Ts
import { z } from 'zod'
import { FastifyPluginAsyncZod } from 'fastify-type-provider-zod'

export const subscribeToEventRoute:  = async (app) => {
	app.post('/subscriptions', {
		schema: {
			body: z.object({
				name: z.string(),
				email: z.string().email(),
			}),
		response: {
			201: z.object({
				name: z.string(),
				email: z.string().email(),
			})
		},
	}
	})
}
```
- Agora voltamos ao arquivo do servidor e registramos a nossa rota:
```ts
app.register(route)
```
- Agora vamos configurar as variáveis ambiente, para fazer isso na raiz do nosso projeto vamos criar o arquivo `.env` e dentro dele vamos fazer:
```.env
PORT=3333
```
- Agora voltamos ao arquivo `package.json`, e mudamos o script `dev`, para:
```json
"dev": "tsx watch --env-file=.env src/server.ts"
```
- Mas é bom validarmos essas variáveis ambiente, para isso, dentro da pasta `src`, vamos criar o arquivo `env.ts`e dentro dele vamos fazer da seguinte maneira:
```ts
import { z } from 'zod'

const envSchema = z.object({
	PORT: z.coerce.number().default(3333),
})

export const env = envSchema.parse(process.env)
```
- E agora usamos o arquivo `.env.ts` quando formos usarmos variáveis ambiente;
- Agora vamos instalar o `biome`, para isso usamos o comando:
```zsh
npm i @biomejs/biome -D
```
- Após a instalação na raiz do nosso projeto criamos o arquivo `biome.json`e colocamos as seguintes configurações nele:
```json  
{
  "$schema": "./node_modules/@biomejs/biome/configuration_schema.json",
  "organizeImports": {
    "enabled": true
  },
  "formatter": {
    "indentStyle": "space",
    "indentWidth": 2,
    "lineWidth": 80
  },
  "javascript": {
    "formatter": {
      "arrowParentheses": "asNeeded",
      "jsxQuoteStyle": "double",
      "quoteStyle": "single",
      "semicolons": "asNeeded",
      "trailingCommas": "es5"
    }
  },
  "linter": {
    "enabled": true,
    "rules": {
      "recommended": true
    }
  },
  "files": {
    "ignore": [
      "node_modules"
    ]
  }
}
```
- E agora para rodar o `biome`, abrimos as configurações desse projeto e no arquivo que irá gerar de maneira automática colocamos:
```json
{
	"editor.formatOnSave": true,
	"[typescript]": {
		"editor.defaultFormatter": "biomejs.biome"
	},
	"editor.codeActionsOnSave": {
		"source.organizeImports.biome": "explicit"
	}
}
```