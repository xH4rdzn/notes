___
- Podemos navegar de outras maneiras além do *link*, como através de botões;
- Para fazer isso seguimos o exemplo abaixo:
```tsx
import { useNavigate } from 'react-router'

export function Home() {
	const navigate = useNavigate()

	return (
		<div>
			<h1>Página Home</h1>
			
			<button 
				type="button"
				onClick={() => navigate("/products")}
			>
				Ver Produtos
			</button>
			
		</div>
	)
}
```
- Desta maneira conseguimos navegar usando outras maneiras além do *link*;