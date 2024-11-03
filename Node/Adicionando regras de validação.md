___
- De vez fazermos diversos `if`, para validar os dados, e com o `zod`, isso fica muito simples.
- Podemos fazer dessa maneira:
```ts
const bodySchema = z.object({
	name: z.string({required_error: "Name is required!"}).min(6),
	price: z.number()
})
```
- `min()` -> A quantidade mínima de caracteres ou números
- `trim()` -> Não conta os espaços em branco
- `positive()`-> Não permite números negativos