___
- Com `typeof`, podemos definir tipagens a partir de outras tipagens, como é demonstrado no exemplo abaixo:
```ts
interface Product {
	id: number
	name: string
}

const product1: Product = { id: 1, name: "Produto 1"}

// Usando o typeof
const product2: typeof product1 = { id: 2, name: "Produto 2"}
```
