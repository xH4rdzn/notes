___
- Podemos ter [[Eventos|eventos]] em elementos específicos;
- Para isso vamos selecionar o elemento específico que queremos observar os eventos:
```js
const ul = document.querySelector("ul")
```
- E agora vamos adicionar o método `addEventListener`;
```js
ul.addEventListener("scroll", (event) => {
	console.log(event)
})
```
- **Scroll** é o nome do evento que vamos observar no elemento selecionado;
- Podemos manipular qualquer atributo do evento, inclusive a posição, como no exemplo abaixo que vamos fazer voltar ao inicio da lista quando chegar no final dela;
```js
const ul = document.querySelector("ul")

ul.addEventListener("scroll", () => {
	if(ul.scrollTop > 300) {
		ul.scrollTo({
			top: 0,
			behavior: "smooth"
		})
	}
})
```
- Podemos escolher qualquer elemento do [[DOM - Document Object Model|DOM]], para poder observar os eventos ocorridos especificamente nesse elemento.