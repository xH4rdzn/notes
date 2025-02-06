___
- Para criar uma aplicação node, podemos usar o comando abaixo:
```zsh
npm init -y
```
- Após criarmos o projeto, podemos instalar o *Typescript*, como visto [[Entendendo o Typescript|anteriormente]];
- Após a instalação do *Typescript* e sua configuração, podemos criar a pasta `src`;
![[Pasted image 20250125194752.png]]
- Agora dentro da pasta `src`, podemos criar um arquivo com o nome de `server.ts`
![[Pasted image 20250125194908.png]]
- E também podemos instalar o **Fastify**, usando o comando:
```zsh
npm i fastify
```
- Após a instalação do **Fastify**, precisamos fazer sua importação no arquivo `server.ts`, da seguinte maneira:
```ts
import fastify from 'fastify'
```
- Após fazer a importação criarmos uma **constante**, para armazenar uma instancia do *fastify*;
```ts
const app = fastify()
```
- Agora a partir de variável `app`, podemos fazer as funcionalidades básicas de uma aplicação web, como no exemplo abaixo que vamos fazer uma rota que vai devolver um *`Hello World`*
	- O primeiro parâmetro é o endereço desse recurso
	- O segundo parâmetro é uma função, o que aquela rota executa.
```ts
app.get('/hello', () => {
	return 'Hello World'
})
```
- E agora para disponibilizarmos uma porta, para rodar esse servidor localmente usamos o método `listen`, e passamos a porta desejada para a função, como no exemplo a seguir:
```ts
app.listen({
	port: 3333,
}).then(() => {
	console.log('HTTP Server Running!')
})
```
- Como estamos usando o *Node* com *Typescript*, é necessário instalar as tipagens do *Node*, para isso usamos o comando abaixo:
```zsh
npm i -D @types/node
```
- Porém ainda para poder executar o código seria necessário buildar o arquivo de *Typescript* para *Javascript*, mas para podermos evitar isso vamos usar a biblioteca do `tsx`, que instalamos usando o comando abaixo:
```zsh
npm i tsx -D
```
- Com o **TSX**, conseguimos executar o arquivo diretamente com *Typescript*;
- Vamos criar um **script**, para poder automatizar a execução do *tsx*
```json
{
	"scripts": {
		"dev": "tsx watch src/server.ts"
	}
}
```
- Agora para executar o nosso servidor **HTTP**, usamos o comando abaixo:
```zsh
npm run dev
```
