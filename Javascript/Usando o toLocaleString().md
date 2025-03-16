___
- Esse método podemos usar para formatar datas de acordo com a formatação de onde estamos:
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toLocaleString())
```
- Mas também podemos utilizar ele para formatar de acordo com um padrão, como no exemplo:
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toLocaleString("pt-BR"))
```
- Mas também podemos passar como segundo parâmetro um objeto de configurações adicionais, como no exemplo abaixo:
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toLocaleString("pt-BR", {
	dateStyle: "short",
}))

// Irá retornar -> 02/07/2024
```
- Se usarmos o `long`, ele irá retornar da seguinte maneira:
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toLocaleString("pt-BR", {
	dateStyle: "long",
}))

// Irá retornar -> 02 de julho de 2024
```
- Se usarmos o `medium`, ele irá retornar da seguinte maneira:
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toLocaleString("pt-BR", {
	dateStyle: "medium",
}))

// Irá retornar -> 02 de jul. de 2024
```
- Se usarmos o `full`:
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toLocaleString("pt-BR", {
	dateStyle: "full",
}))

// Irá retornar -> terça-feira, 2 de julho de 2024
```
- Também podemos configurar o `day`, podemos configurar se vai ser numérico ou se vai ter dois dígitos
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toLocaleString("pt-BR", {
	day: "2-digit",
	month: "2-digit",
	hour: "2-digit",
	minute: "2-digit",
}))
```
- Também podemos usar o `toLocaleString`, para formatar números, como no exemplo abaixo:
```js
let amount = 12.5

console.log(amount.toLocaleString("pt-BR", {
	style: "currency",
	currency: "BRL",
}))

// Irá retornar -> R$ 12,50
```
