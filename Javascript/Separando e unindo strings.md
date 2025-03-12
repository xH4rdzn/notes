___
- Podemos separar as *Strings*, usando o método `split`;
- No qual passamos como parâmetro onde queremos que seja separado cada palavra
```js
let text = "Estudar, Aprender, Praticar"
let separate = text.split(",")

console.log(separate)
// Retorna um array com todas as palavras que foram separadas;
```
- Para podermos unir a *string*, usamos o método `join`;
- Se não passarmos nada para esse método, ele retorna a *String* ao jeito que ela era normalmente
```js
let joined = separate.join()
```
- Mas também podemos passar alguma coisa para ele *dar espaço entre as palavras*
```js
let joined = separate.join(" - ")
console.log(joined)

// Estudar - Aprender - Praticar 
```
