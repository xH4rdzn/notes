___
- Na nota anterior vimos como funciona a [[Conhecendo sobre imutabilidade|imutabilidade]], agora vamos fazer um exemplo prático;
```js
const address1 = {
	street: "Av. Brasil",
	number: 20,
}

// Isso não é uma cópia. É uma referência.
const address2 = address1
```
- No exemplo acima, se alterarmos alguma propriedade do objeto `address2`, ele vai alterar no `address1`também;
- Para fazer uma cópia do objeto usamos o [[Conhecendo o spread|spread operator]];
```js
const address1 = {
	street: "Av. Brasil",
	number: 20,
}

const address2 = {...address1}
address2.number = 30
```
- No exemplo acima, vai alterar a propriedade `number`, apenas no objeto `address2`;
- Podemos também alterar propriedades diretamente em sua cópia, como demostrado no exemplo abaixo:
```js
const address1 = {
	street: "Av. Brasil",
	number: 20,
}

const address2 = {...address1, number: 30}
```
- Agora vamos ter um exemplo com *arrays*
```js
// Isso é uma referência
const list1 = ["Apple", "Banana"]
const list2 = list1
```
- Para criar uma cópia de um *array*, podemos fazer da seguinte maneira:
```js
// Criando uma cópia de list1
const list1 = ["Apple", "Banana"]
const list2 = [...list1]

// Adicionando um novo item, no momento da cópia
const list2 = [...list1, "Watermelon"]
```


