___
- Usamos esses operadores principalmente para tomada de decisão em nossa aplicação
- Operador *AND (E)*: `&&`
	- Nesse operador ambas as comparações precisam resultar em true, para ele ser true;
```js
let email = true
let password = true

console.log(email && password)
```
- Operador *OR (OU)*: `||`
	- Nesse operador apenas uma das comparações precisam resultar em `true`, para poder passar nessa avaliação
```js
console.log(email || password)
```
- Operador *NOT (negação)*: `!`
	- Com esse operador conseguimos inverter um valor, caso ele seja `true`, usamos esse operador e ele vai se tornar `false`
```js
console.log(!true)
```