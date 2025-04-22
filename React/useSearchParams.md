___
- Também podemos passar parâmetros para uma rota:
```tsx
export function Home(){
	return (
		<div>
			<h1>Página Home</h1>

			<nav>
				<a href="/products">Produtos</a>
				<a href="/products?category=tvs">Categoria</a>
			</nav>
		
		</div>
	)
}
```
- Agora em nosso arquivo que leva para a página `Products`, podemos recuperar esses parâmetros:
```tsx
import { useSearchParams } from 'react-router'

export function Products() {
	const [searchParams] = useSearchParams()
	const category = searchParams.get("category")

	return (
		<div>
			<a href="/">Voltar</a>

			<h1>Produtos</h1>

			{
				category && (
					<span>
						Categoria <strong>{category}</strong>
					</span>
				)
			}
		
		</div>
	)
}
```