___
- Podemos formatar uma data, como pegar os dias, entre os dias 1 e 9 ele retorna apenas 1 número, então podemos fazer a formatação para que ele retorne 2 números, como no exemplo abaixo:
```js
let date = new Date("2025-07-02T14:30:00")

console.log(date.getDate()) // Retorna apenas "2"

// Fazemos a formatação usando o método padStart, mas antes precisamos transformar esse número em string
console.log(date.getDate().toString().padStart(2, "0"))
```
- Podemos fazer isso para o mês também, porém o mês em *javascript* vai entre 0 e 11, então precisamos fazer da seguinte maneira:
```js
console.log((date.getMonth() + 1).toString().padStart)
```
- Podemos fazer um padrão para a nossa aplicação:
```js
let year = date.getFullYear()
let hour = date.getHours()
let minutes = date.getMinutes()

console.log(`${day}/${month}/${year} às ${hour}:${minutes}`)
```
