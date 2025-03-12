____
- Também conseguimos modificar a data e a hora
```js
let date = new Date("July 3, 2024 14:30:00")

// Modificar o ano
date.setFullYear(2030)

// Modificar o mês (0 à 11)
date.setMonth(7)

// Modificar o dia
date.setDate(10)
```
- Também podemos modificar a hora
```js
let date = new Date("July 3, 2024 14:30:00")

// Modificar a hora
date.setHours(18)

// Modificar os minutos
date.setMinutes(15)

// Modificar os segundos
date.setSeconds(30)
```