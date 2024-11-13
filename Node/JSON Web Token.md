___
- Para podermos usar o `JSON Web Token`, precisamos fazer a instalação em nossa aplicação, para isso usamos o comando abaixo:
```zsh
npm i jsonwebtoken
```
- E precisamos instalar a tipagem, usando o comando:
```zsh
npm i @types/jsonwebtoken -D
```
- Agora dentro da pasta `src`, vamos criar uma pasta com o nome de `configs`, e dentro dessa pasta criamos o arquivo `auth.ts`
- Dentro do arquivo `auth.ts`, fazemos as seguintes configurações:
```ts
export const authConfig = {
	jwt: {
		secret: process.env.AUTH_SECRET || "default",
		expiresIn: "1d",
	},
}
```
- A propriedade `secret`, recebe a nossa variável de ambiente, caso ela não carregue usamos o valor `default`;
- A propriedade `expiresIn`, é o tempo que esse token vai demorar para expirar;