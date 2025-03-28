___
- Podemos sobrescrever `interface`, mas não podemos fazer isso com `type`
```ts
interface IProduct extends IBaseProduct {
	id: number,
	name: string
}

interface IProduct {
	quantity: number
}
```
- Quando fazemos como no exemplo acima, ele unifica as duas interfaces;
- No caso do `type`, conseguimos dar a ele tipos primitivos, em `interface`não