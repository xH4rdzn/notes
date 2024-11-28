___
- Como exemplo vamos criar uma função de soma e fazer o teste dela;
```ts
export function sum(a: number, b: number) {
	return a + b
}
```
- No arquivo de testes, vamos usar da seguinte maneira:
```ts
import { sum } from "./sum"

test("sum", () => {
	const result = sum(3, 7)

	expect(result).toBe(10)
})
```
*Para a função `expect`, passamos o retorno que esperamos*;
*Para o `toBe`, passamos o resultado que estamos esperando*;
- No exemplo nota-se que estamos passando o resultado do retorno da função `sum`e esperamos que o resultado seja *10*;
- *Sempre bom simular um teste que dê erro, para validar se não está dando um falso positivo;*