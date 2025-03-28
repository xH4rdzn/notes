___
- Podemos também tipar funções, seus parâmetros e seu retorno, como é demostrando no exemplo abaixo:
```ts
// Tipando os parâmetros
function sum(x: number, y: number) {
	const result = x + y
}
```
- Quando uma função não tem retorno, o tipo de retorno é inferido automaticamente como `void`, mas também podemos definir isso de maneira explicíta
```ts
function sum(x: number, y: number): void {
	// código
}
```
- Quando temos um retorno, podemos deixar que o *Typescript* deduza o tipo de retorno, ou podemos também deixar de maneira explicíta
```ts
function sum(x: number, y: number): number {
	const result = x + y
	return result
}
```
- Podemos também tipar *arrow functions*, como demostrado no exemplo:
```ts
const showMessage = (name: string): string => {
	const message = "Olá " + name

	return message
}
```