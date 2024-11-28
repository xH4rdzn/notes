___
- Além de usarmos a função `test()`, para criarmos nossos testes, podemos também usar a função `it()`, eles fazem a mesma coisa;
```ts
it("should do sum of 3 + 7 must be 10", () => {
	const result = sum(3, 7)

	expect(result).toBe(10)
})
```
*A única diferença está na semântica*;