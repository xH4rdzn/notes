___
- No *React*, temos outra regra, é que um componente não pode devolver vários componentes de uma vez;
- Um componente tem que devolver um elemento pai, e quantos filhos ele quiser retornar;
- Para resolver isso, podemos devolver os componentes dentro de um elemento HTML, como no exemplo abaixo:
```tsx
export function App() {
	return (
		<div>
			<Button />
			<Button />
		</div>
	)
}
```
- Ou então podemos usar o `fragment`, que não tem nenhum impacto visual em nossa aplicação:
```Tsx
export function App() {
	return (
		<>
			<Button />
			<Button />
		</>
	)
}
```