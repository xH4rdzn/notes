___
- Agora vamos continuar modificando o input, para ele aceitar apenas números, para isso vamos usar uma `regex`, então fazemos como no exemplo:
```js
amount.oninput = () => {
	let value = amount.value.replace(/\D/g, "")

	amount.value = value
}
```
- Usamos a `regex`-> `/\D/g`, para não aceitar caracteres;
- E depois repassamos o valor formatado para `amount.value`