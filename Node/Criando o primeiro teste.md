___
- Para criar os nossos testes vamos utilizar o *Vitest*, para instalar ele usamos o comando:
```zsh
npm i vitest -D
```
- Na raiz do nosso projeto podemos criar uma pasta com o nome `test`.
- Dentro dessa pasta vamos criar os arquivos que vão conter nossos testes.
- Para nomear esses arquivos usamos o `example.spec.ts`ou `example.test.ts`, é escolha de gosto, mas precisam ser uma das duas.
- Dentro do arquivo criado, fazemos como no exemplo abaixo:
```ts
import { test, expect } from 'vitest'

test('O usuário consegue criar uma nova transação', () => {

	const responseStatusCode = 201

	expect(responseStatusCode).toEqual(201)
})
```
- *Todos os testes precisam da etapa de validação*
- Para executar os nossos testes agora rodamos o comando:
```zsh
npx vitest
```
- Podemos criar um **script** para poder automatizar esse comando, no arquivo `package.json`, criamos:
```json
{
 "scripts": {
	 "test": "vitest",
 }
}
```
- E agora podemos usar o comando:
```zsh
npm run test
```
- Ou:
```zsh
npm test
```
- Para executar esse **script**