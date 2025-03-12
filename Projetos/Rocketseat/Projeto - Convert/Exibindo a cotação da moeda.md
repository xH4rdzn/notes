___
- Quando exibimos o `footer`, percebemos que está um valor fixo, que foi setado no próprio HTML;
- Para tornar isso de maneira dinâmica, podemos selecionar o elemento que está com a descrição da moeda, para isso usamos:
```js
const description = document.getElementById('description')
```
- Após selecionar o elemento que está com a cotação da moeda, vamos alterar o seu conteúdo, para isso vamos usar da seguinte maneira:
```js
description.textContent = `${symbol} 1 = ${price}`
```
- *O código acima deve estar dentro do bloco `try-catch`que está dentro da função `convertCurrency`*
- Desta maneira já ficará dinâmico os valores que irão aparecer no `footer`;
