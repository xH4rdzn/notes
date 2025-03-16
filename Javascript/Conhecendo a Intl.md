___
- **Intl** é a API de internacionalização do ECMAScript.
- Como podemos ver no exemplo abaixo:
```js
// Obtém informações da localidade

const currentLocale = Intl.DateTimeFormat().resolvedOptions()
```
- Também podemos usar essa API, para fazer formatação
```js
// Formata de acordo com a localidade

console.log(new Intl.DateTimeFormat("pt-BR").format(new Date()))
```
- Também podemos usar o `Intl`, para verificar a diferença entre as timezone.
```js
// Obtém a diferença em minutos do timezone.
console.log(date.getTimezoneOffset())

// Obtém a diferença em horas do timezone.
console.log(date.getTimezoneOffset() / 60)
```