___
- Vamos começar a escrever os testes, para isso vamos fazer a instalação do `vitest`, para isso vamos utilizar o comando:
```zsh
npm i vitest vite-tsconfig-paths -D
```
- Agora na raiz do nosso projeto vamos criar um arquivo com o nome de `vitest.config.ts` e dentro dele vamos:
```ts
import { defineConfig } from 'vitest/config'
import tsconfigPaths from 'vite-tsconfig-paths'

export default defineConfig({
	plugins: [tsconfigPaths()],
})
```
- Agora no arquivo `package.json`vamos criar um *script* para rodar os testes:
```json
"test": "vitest run",
"test:watch": "vitestd"
```
