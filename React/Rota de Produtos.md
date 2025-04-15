___
- Agora vamos criar uma nova rota, dentro da pasta `pages`, vamos criar o arquivo `Products.tsx`e dentro dele fazemos:
```tsx
export function Products() {
	return (
		<div>
			<h1>Produtos</h1>
		</div>
	)
}
```
- Agora dentro do arquivo `AppRoutes`, importamos esse arquivo da seguinte maneira:
```tsx
import { Products } from '../pages/Products'

// Adicionando a Rota

	<Route path="/products" element={<Products />} />
```