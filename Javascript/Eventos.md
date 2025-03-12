___
- Com o javascript também conseguimos lidar com eventos;
- Os eventos são os usuários que fazem uma interação com a nossa página;
- Para adicionar um **evento**, usamos o método `addEventListener`;
```js
window.addEventListener("load", () => {
	console.log("A página foi carregada")
})
```
- O primeiro parâmetro é o evento que queremos observar;
- O segundo parâmetro é uma função para realizar algo quando o evento é realizado;
- Para tirar um comportamento padrão de algum elemento podemos usar o método `preventDefault`
- Se quisermos recuperar o elemento no qual ocorreu o evento, usamos:
```js
addEventListener("click", (event) => {
	event.preventDefault()

	// Retorna o elemento clicado
	console.log(event.target)
})
```
- Podemos também recuperar os atributos que estão dentro desse elemento:
```js
addEventListener("click", (event) => {
	event.preventDefault()

	// Retorna o textContent do elemento clicado
	console.log(event.target.textContent)
})
```
