___
- Assim como temos o [[beforeAll]], temos o `AfterAll`, que executa uma função após os testes;
```ts
afterAll(() => {
	sumResult = 0
	console.log("Executado depois dos testes")
})
```
