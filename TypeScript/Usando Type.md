___
- Podemos usar o `Type`, para criar tipos personalizados, assim como as [[Conhecendo interface no Typescript|interfaces]], como demostrado no exemplo abaixo:
```ts
type Product = {
	id: number,
	name: string
}

function newProduct(product: Product) {}

```
- Outro recurso interessante do `type`é utilizar ele para criar uma tipagem separada e fazer a *união de tipos*, como no exemplo abaixo:
```ts
type SelectResponse = Product[] | null
```