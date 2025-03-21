___
- Agora que o nosso *input* aceita apenas valores numéricos, podemos fazer uma função separada para formatar o valor para a maneira que estamos acostumados
```js
function formatCurrencyBRL(value) {
	value = value.toLocaleString("pt-BR", {
		style: "currency",
		currency: "BRL",
	})

	return value
}
```
- Mas antes de atualizar o valor no input, precisamos transformar o valor digitado em centavos, para que ele aplique a formatação, para fazer isso fazemos isso:
```js
value = Number(value) / 100
```
- E agora passamos para atualizar o valor do input:
```js
amount.value = formatCurrencyBRL(value)
```
