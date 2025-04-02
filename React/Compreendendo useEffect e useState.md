___
### useEffect
- Utilizado no ciclo de vida do componente quando o componente é renderizado. E permite trabalhar com side-effects (efeitos colaterais).
- *`useEffect` precisa estar dentro de um componente*.
- Utilizamos o `useEffect` dentro do componente para ter acesso aos estados do componente.
```ts
export function MyComponent() {
	const [name, setName] = useState("")

	useEffect(() => {
		searchMyName()
	}, [name])

	return (
		// Código
	)
}
```