___
- Podemos também fazer a tipagem de objetos, para fazer a tipagem de objetos, podemos fazer como no exemplo abaixo:
```ts
let user: { name: string, age: number} = {name: "Igor", age: 26}
```
- Para deixar uma propriedade de maneira opcional, podemos fazer da seguinte maneira:
```ts
let user: {name: string, age:number, avatarUrl?: string} = {}
```
- Passamos o `?`, isso significa que essa propriedade é opcional;
- Para funções podemos passar da seguinte maneira:
```ts
// Maneira desestruturada
function signIn({ email, password}: {email: string, password: string})
```
- Ou também podemos retirar tudo apenas de um local
```ts
function signIn(user :{email:string, password: string}) {}
```
