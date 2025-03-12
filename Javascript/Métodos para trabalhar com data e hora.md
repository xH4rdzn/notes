___
- Temos vários métodos para se trabalhar com data e hora, por exemplo, se quisermos saber que dia da semana vai cair tal data, podemos fazer como no exemplo:
```js
let date = new Date("2025-09-14T14:20:00")

console.log(date.getDay())
```
- O método `getDay()`, retorna os dias da semana de 0 à 6, *onde domingo é 0*
- Conseguimos também recuperar apenas o dia com o método `getDate()`
```js
let date = new Date("2025-09-14T14:20:00")

// Dia do mês (0 à 30)
console.log(date.getDate())
```
- Para mês:
```js
let date = new Date("2025-09-14T14:20:00")

// Dia do mês (0 à 11)
console.log(date.getMonth() + 1)
```
- *Nota-se que usamos `+1`, pois ele conta de 0 à 11, então para termos o número do mês exato somamos `+1`*
- Para o ano:
```js
let date = new Date("2025-09-14T14:20:00")

// Ano
console.log(date.getFullYear())
```
- Para pegar horas:
```js
let date = new Date("2025-09-14T14:20:00")

// Horas
console.log(date.getHours())
```
- Para minutos:
```js
let date = new Date("2025-09-14T14:20:00")

// Minutos
console.log(date.getMinutes())
```
- Segundos:
```js
let date = new Date("2025-09-14T14:20:00")

// Segundos
console.log(date.getSeconds())
```