___
- Como passamos o nosso `secret`, através de um arquivo `.env`, ele pode não existir, para isso precisamos validar que essa variável exista, para fazer isso vamos utilizar o `zod`;
- Para fazer isso, dentro da pasta `src`, vamos criar um arquivo com o nome de `env.ts`e dentro desse arquivo fazemos da seguinte maneira:
```ts
import { z } from "zod"

const envSchema = z.object({
	DATABASE_URL: z.string().url(),
	JWT_SECRET: z.string()
})

export const env = envSchema.parse(process.env)
```
- Agora voltamos ao arquivo `auth.ts`, e em vez de usarmos diretamente usamos da seguinte maneira:
```ts
import { env } from "../env"

export const authConfig = {
	jwt: {
		secret: env.JWT_SECRET,
		expiresIn: "1d",
	},
}
```
- Agora no nosso controller ele não irá reclamar mais.
