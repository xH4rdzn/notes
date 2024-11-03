___
- É um método do `zod`, para dizer que não pode ser `nulo`, ou seja um campo opcional.
- Passamos da seguinte maneira:
```ts
const bodySchema = z.object({
	name: z.string(),
	price: z.number().nullish()
})
```