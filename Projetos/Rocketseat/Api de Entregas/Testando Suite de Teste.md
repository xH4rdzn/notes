___
- Agora que [[Configurando o Jest|configuramos o jest]], dentro da pasta `src`, podemos criar uma pasta com o nome de `tests`, essa pasta irá armazenar os arquivos dos testes;
- O primeiro arquivo de testes que vamos criar é o `usersController.test.ts`;
```ts
describe("UsersController", () => {
	console.log("Passou por aqui")
})
```
- Mas antes de testarmos, precisamos adicionar o *script*, para poder rodar os testes, então no arquivo `package.json` vamos adicionar o seguinte:
```json
{
	"scripts": {
		"test:dev": "NODE_OPTIONS=--experimental-vm-modules npx jest --watchAll --runInBand"
	}
}
```
- E também precisamos instalar a biblioteca `ts-node`, para isso vamos utilizar o comando:
```zsh
npm i ts-node -D
```
- Agora podemos rodar o comando:
```zsh
npm run test:dev
```