___
- Podemos manipular o conteúdo dos elementos, para fazermos isso selecionamos o elemento e acessamos sua propriedade, como no exemplo abaixo:
```js
const guest = document.querySelector("#guest-1")

guest.textContent = "Novo valor"
```
- Quando usamos o `textContent`, ele substitui tudo pelo texto, inclusive as tags
- Se quisermos manter a tag devemos selecionar ela também, como no exemplo a seguir:
```js
const guest = document.querySelector("#guest-1 span")
```
- Além do `textContent`temos mais dois métodos o `innerText`e o `innerHTML`;
- O `innerText`retorna o texto do elemento sem formatação (conteúdo visível);
- O `innerHTML`retorna o HTML do elemento em forma de texto;
- O `textContent`retorna o conteúdo visível e oculto.