___
- Podemos criar os nossos próprios Hooks;
- O Hook é uma função com o padrão `useNomeDoHook`
- Para fazer isso de maneira separada na pasta `src`, criamos a pasta `hooks`, e lá colocamos todos os hooks criado por nós, como no exemplo abaixo:
```ts
export function useMessage() {
	function show() {
		console.log("Mensagem do meu próprio hook")
	}
}
```
- *Todos os Hooks, devem ter extensão `.ts`*
- Podemos passar parâmetros tanto para o hook, como para as funções internas do hook
```ts
type Props = {
	name: string
}

export function useMessage({ name }: Props) {
	function show(message) {
		console.log(name, message)
	}
}
```
- E quando formos usar o hook, passamos a propriedade como um objeto:
```ts
const message = useMessage({ name: "Igor" })
```