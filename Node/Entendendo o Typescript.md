___
- Vamos utilizar o *Typescript* em nossas aplicações Node;
- Para poder usar ele precisamos iniciar o projeto usando o comando:
```zsh
npm init -y
```
- Com o *Typescript*, podemos criar tipos para o que precisarmos, como no exemplo abaixo que vamos criar uma `interface`do tipo `User`
```ts
interface User {
	birthYear: number
}
```
- Para instalar o *Typescript*, usamos o comando abaixo:
```zsh
npm i typescript -D
```
- Com o *Typescript* instalado, precisamos inicializar as configurações dele, para isso usamos o comando abaixo:
```zsh
npx tsc --init
```
- Ao executar o comando acima, irá gerar um arquivo com o nome de `tsconfig.json`;
- Esse arquivo possui várias configurações do *Typescript*, uma das configurações mais importantes é a `target`, podemos por no mínimo a opção `ES2020`;