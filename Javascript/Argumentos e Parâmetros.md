___
- **Parâmetros**: é a variável (escopo da função) que irá receber um valor em uma função;
- **Argumentos**: é o valor que é passado para a função;
- Para passar uma parâmetro fazemos da seguinte maneira:
```js
function message(username) {
	console.log("Olá", username)
}
```
- E passamos argumentos da seguinte maneira:
```js
message("Igor")
```
- Podemos definir valores padrões para os parâmetros, para isso fazemos como nos exemplo abaixo:
```js
function joinText(text1, text2= "valor") {
	console.log(text1, text2)
}
```
- Agora caso não passarmos o segundo argumento ele irá usar o valor padrão;
