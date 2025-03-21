___
- No projeto, temos um `input`, que temos que colocar os valores da despesa, ele deve aceitar apenas números, porém no momento ele está aceitando letras também, para resolver isso vamos usar javascript.
- Então vamos selecionar o `input`
```js
const amount = document.getElementById('amount')
```
- Após selecionar o elemento, vamos observar os eventos:
```js
amount.oninput = () => {}
```
- Vamos usar o evento `oninput`, pois ele observa todo tipo de entrada de dados no *input*;
- Desta maneira já temos o *input* selecionado e também o evento que vamos observar agora precisamos que o [[Aceitando somente números no valor|input aceite apenas números]]