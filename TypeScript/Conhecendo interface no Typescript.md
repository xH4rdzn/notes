___
- Usamos as `interface`, para poder criar um tipo personalizado, para criar uma interface, usamos a *keyword* `interface`, seguindo o exemplo:
```ts
interface Product {
	id: number,
	name: string
}
```
- E agora podemos passar essa tipagem para variáveis, funções e etc, como no exemplo abaixo:
```ts
interface Product {
	id: number,
	name: string
}

// Passando a interface como tipagem para parâmetro de função
function newProduct(product: Product) {}
```

