___
- Podemos criar rotas com parâmetros;
- Para isso podemos criar uma página como visto anteriormente:
```tsx
// Details.tsx

export function Details() {
	return (
		<div>
			<h1>Detalhes</h1>
		</div>
	)
}
```
- Agora no arquivo onde estamos colocando as nossas rotas, colocamos da seguinte maneira:
```tsx
//AppRoutes.tsx

<Route path="/details/:id" element={<Details />}/>
```