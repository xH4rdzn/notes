___
- Como já estamos [[Obtendo o valor digitado]] do `input`, agora precisamos validar que ele vai receber apenas números;
- Para isso podemos usar uma expressão regular para validar isso;
- Vamos fazer da seguinte maneira:
```js
amount.addEventListener("input", () => {
	
	const hasCharactersRegex = /\D+/g
	amount.value = amount.value.replace(hasCharactersRegex, "")
})
```
- Desta maneira o `input`, vai aceitar só números, mesmo que digite letras nele, o valor irá ser substituído por apenas números; 