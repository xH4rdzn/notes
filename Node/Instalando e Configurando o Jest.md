___
- Para instalar o `Jest`, usamos o comando abaixo:
```zsh
npm i jest -D
```
- Como estamos usando o `typescript`, precisamos também instalar a tipagem do `Jest`, usando o comando abaixo:
```zsh
npm i @types/jest -D
```
- E precisamos também instalar outro pacote, para escrever os nossos testes em `typescript`, usando o comando abaixo:
```zsh
npm i ts-jest -D
```
- Após a instalação, precisamos inicializar o `Jest`, para isso podemos criar um arquivo manualmente ou usar o comando:
```zsh
npx jest --init
```
*E respondemos as perguntas que irão aparecer*
- Para criar esse arquivo manualmente, vamos criar o arquivo `jest.config.ts` na raiz do nosso projeto;
- Nesse arquivo vamos fazer a seguinte configuração:
```ts
import type { Config } from "jest"

const config: Config = {
	bail: true, // Para a execução dos testes caso um falhe
	preset: "ts-jest",
	testEnvironment: "node"
}

export default config
```
*Inicialmente o `JEST`está configurado*
- Precisamos também instalar o `ts-node`, por conta do `typescript`:
```zsh
npm i ts-node -D
```