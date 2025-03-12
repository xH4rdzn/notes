___
- Onde devolvemos o valor vamos utilizar *interpolação de strings*
```js
result.textContent = `${total} Reais`
```
- Como criamos a função para formatar para reais, podemos fazer o uso dela e depois remover o `R$`:
```JS
total = formatCurrencyBRL(total).replace("R$", "")
```
- Desta maneira já deve ficar como queremos que seja exibido;
