___
- Anteriormente criamos uma [[Criando uma API de exemplo|API de exemplo]], agora vamos aprender a consumir essa API, utilizando o `fetch`, utilizando o `then`;
```js
// fetch("endereço da API que queremos consumir")

fetch("http://localhost:3333/products")
.then((response) => response.json())
.then((data) => console.log(data))
```