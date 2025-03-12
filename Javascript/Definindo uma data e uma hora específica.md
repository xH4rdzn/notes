___
- Podemos definir uma data e hora específica, para isso podemos fazer da seguinte maneira:
```js
console.log(new Date())
```
- A sequência que o `Date`, recebe é a seguinte: ano, mês, dia, como no exemplo abaixo:
```js
console.log(new Date(2025, 6, 3))
```
- O meses, vão de 0 à 11;
- Para definirmos a data e a hora fazemos da seguinte maneira:
```js
console.log(new Date(2024, 6, 3, 14, 30, 0))
```
- Após o *dia*, ele recebe: *hora, minuto e segundo*;
- Outra maneira de definir data e hora é:
```js
console.log(new Date("2024-07-03T14:30:00"))
```
- Porém quando usamos o via *strings*, o mês 7 representa julho;
- Podemos definir data e hora assim também:
```js
console.log(new Date("July, 3, 2025 13:30:33"))
```
