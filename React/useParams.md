___
- Podemos recuperar o parâmetro que passamos na rota, como visto [[Rota com parâmetro|anteriormente]];
- Podemos recuperar o parâmetro passado como no exemplo abaixo:
```tsx
// Details.tsx
import { useParams } from 'react-router'

export function Details() {
	const { id } = useParams()
	return (
		<div>
			<h1>Detalhes</h1>
			<span> ID do produto: <strong>{id}</strong></span>
		</div>
	)
}
```
- Acima, estamos desestruturando o `id`