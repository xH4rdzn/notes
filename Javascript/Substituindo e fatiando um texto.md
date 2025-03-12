___
- Para poder fazer a substituição de partes do texto, usamos o método `replace`;
- Esse método recebe como parâmetro *duas strings*;
- O primeiro parâmetro é o que queremos substituir;
- O segundo parâmetro é o que queremos colocar no lugar do que vamos substituir;
```js
let message = "Estou estudando os fundamentos do Javascript"

console.log(message.replace("Javascript", "HTML"))
```
- **Esse método não altera o valor original da variável**

### Extraindo uma parte da string (start, end)
- Para podermos pegar parte de um texto, podemos usar o método `slice`;
- Esse método recebe números, que é de onde queremos que ele inicie e termine;
```js
console.log(message.slice(6, 30))
```
- Conseguimos fazer de trás para frente;
```js
console.log(message.slice(-11))
```
- Para fazer isso usamos um número negativo;

### Tirando espaços do texto;
- Para tirar os espaços em branco no inicio e no fim dos textos, usamos o método `trim`;
```js
let textWithSpace = "   Texto de Exemplo  "
console.log(textWithSpace.trim())
```