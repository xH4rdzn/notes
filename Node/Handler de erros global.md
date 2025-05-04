___
- Para criar um *handler* global de erros, vamos no arquivo `app.ts`e fazemos o seguinte:
```ts
import fastify from 'fastify'
import { appRoutes } from './http/routes'

export const app = fastify()

app.register(appRoutes)

app.setErrorHandler((error, _, reply) => {
	if(error instanceof ZodError) {
		return reply.status(400).send({ message: 'Erro de validação', issues: error.format()})
	}

	if(env.NODE_ENV !== 'production') {
		console.error(error)
	} else {
		
	}

	return reply.status(500).send({ message: 'Internal server error'})
})
```