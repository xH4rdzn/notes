___
- Como um teste pode testar vários casos, podemos agrupar esses testes, para agrupar usamos a função `describe()`, como no exemplo abaixo:
```ts
describe("sum", () => {
	test("sum of 3 + 7 must be 10", () => {
		const result = sum(3, 7)

		expect(result).toBe(10)
	})

	test("sum of 2 + 2 must be 4", () => {
		const result = sum(2, 2)

		expect(result).toBe(4)
	})
})
```
*Desta maneira os testes ficam agrupados*;