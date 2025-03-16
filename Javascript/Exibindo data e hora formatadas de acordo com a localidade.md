___
- No *javascript* temos um método que formata a data de acordo com a nossa localização;
- Esse método é o `toLocaleDateString()
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toLocaleDateString())
```
- Para o tempo, usamos o método `toLocaleTimeString()`
```js
let date = new Date("2024-07-02T14:30:00")

console.log(date.toLocaleTimeString())
```
- E podemos escolher um formato específico que passamos como parâmetro do `toLocaleDateString()` ou `toLocaleTimeString()
```js

// Para Data
console.log(date.toLocaleDateString("en"))


// Para Tempo
console.log(date.toLocaleTimeString("en"))
```