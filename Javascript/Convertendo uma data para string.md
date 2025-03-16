___
- Podemos usar métodos para transformar uma data em uma string;
- O método `toString()`, converte para string diretamente
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toString())
```
- Já o método `toDateString()`, ele retorna apenas a data
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toDateString())
```
- E também temos métodos específicos para tempo, neste caso usamos o `toTimeString()
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toTimeString())
```