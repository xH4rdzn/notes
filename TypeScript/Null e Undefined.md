___
- Tanto o `Null`como o `Undefined`são tipos primitivos;
- O `Undefined`é um valor primitivo utilizado quando uma variável ainda não teve seu valor atribuído;
```ts
let value: number
console.log(value) // Retorna undefined no console

// Para objetos ele retorna undefined para propriedades que não estão nesse objeto
let user = {
	name: "Igor"
}

console.log(user.email) // Retorna Undefined
```
- O `Null` é utilizado quando queremos definir intencionalmente a ausência de valor;
```ts
let email = null
```