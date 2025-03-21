___
- *Rest Params* (...) -> permite representar um número indefinido de argumentos como um array.
- Exemplo:
```js
function values(...rest) {
	console.log(...rest)
}
```
- Se não usarmos o `...`, ele devolve em uma estrutura de *array*
- Podemos usar isso para nomear parâmetros específicos e pegar todo o restante sem nomear
```js
function values(title, ...args) {
	// Código
}
```