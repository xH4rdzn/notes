___
- Agora vamos configurar o jest em nossa aplicação, vamos iniciar usando o comando:
```zsh
npx jest --init
```
- Após usar esse comando precisamos responder as perguntes que irão aparecer.
- Sequencia sugerida em aula:
	- No
	- Yes
	- Node
	- no
	- v8
	- Yes
- Após isso será gerado um arquivo `jest.config.ts`, na raiz do nosso projeto;
- No arquivo gerado, vamos apagar todos os comentários e vamos deixar o arquivo de configuração da seguinte maneira:
```ts
import type { Config } from "jest"

const config: Config = {
	bail: true,
	clearMocks: true,
	coverageProvider: "v8",
	preset: "ts-jest",
	testEnvironment: "node",
	testMatch: ["<rootDir>/src/**/*.test.ts"],
	moduleNameMapper: {
		"^@/(.*)$*": "<rootDir>/src/$1",
	}
}

export default config
```
- Agora já temos o nosso `jest`configurado;