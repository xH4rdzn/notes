___
- Para criar essa rota, que é o retorno quando acessamos uma rota que não existe;
- Podemos criar na mesma estrutura das outras páginas, seguindo o exemplo:
```tsx
export function NotFound() {
	return (
		<div>
			<h1>Ops! Essa página não existe</h1>
		</div>
	)
}
```
- Agora para usarmos no nosso arquivo de rotas, o usamos da seguinte maneira:
```tsx
import { NotFound } from '../pages/NotFound'

<Routes>
	<Route path="*" element={<NotFound />} />
</Routes>
```