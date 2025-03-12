___
- O tipo `string`serve para podermos armazenar textos
```js
let username = "Igor"
console.log(typeof username)
```
- Sempre que formos definirmos um conteúdo do tipo `string`, temos que usar as `"`, mas também podemos usar `'`, como nos exemplos abaixo:
```js
console.log("Isso é uma string em aspas duplas")

console.log('Uma string com aspas simples')
```
- Devemos usar a aspas simples quando queremos usar a aspas duplas dentro do texto, como no exemplo abaixo:
```js
console.log('Uma string com "aspas duplas" dentro de simples')
```
- Mas também podemos fazer o contrário:
```js
console.log("Uma string com 'aspas simples' dentro de dupla.")
```
- Outra maneira de fazer uma `string`é usando o acentro grave, desta maneira podemos escrever múltiplas linhas:
```js
console.log(`
	Uma string com acento grave permite
	escrever múltiplas linhas.
`)
```