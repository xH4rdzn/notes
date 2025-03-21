___
- Agora vamos criar um método que captura o clique nos items da lista, para isso vamos usar da seguinte maneira:
```js
expenseList.addEventListener("click", function(event) {
	if(event.target.classList.contains("remove-icon")){
		
	}
})
```
- Podemos ver que usamos o `event.target`, para escolher um *alvo*, neste caso o que identifica cada botão `X`em nossa aplicação é uma classe, para isso usamos o `classList`, e usamos o método `contains`, para verificar se onde estamos clicando existe essa classe;
- Agora temos como identificar qual item que queremos [[Removendo um item da lista|remover da lista]];
