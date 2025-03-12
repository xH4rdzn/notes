___
- Outra coisa que é possível, é manipular os atributos dos elementos através do javascript;
- Para fazer isso seguimos com o exemplo:
```js
// Selecionando o elemento
const input = document.querySelector("input")

// Adicionando um novo atributo ao elemento selecionado
input.setAttribute("disabled", true)
```
- Podemos também remover atributos, para isso fazemos como no exemplo:
```js
// Removendo um atributo do elemento selecionado
input.removeAttribute("id")
```
