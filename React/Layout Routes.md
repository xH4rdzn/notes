___
- Existem aplicações que tem elementos que são compartilhados entre rotas;
- Para criar essa *Layout Route*, vamos criar uma pasta dentro `src`, com o nome de `components`, e dentro dessa pasta vamos criar outra pasta com o nome de `Layout`, e dentro dessa pasta vamos criar o `index.tsx`e o arquivo de estilização;
- Agora dentro do nosso arquivo `index.tsx`, vamos fazer o seguinte:
```tsx
import './styles.css'

import { Outlet } from 'react-router'

export function Layout() {
	return (
		<div>
			<header>
				<p>Olá, Igor</p>
			</header>

			<Outlet />

			<footer>
				<span>Todos os direitos reservados</span>
			</footer>
		</div>
	)
}
```
- Agora o `header`e o `footer`, estarão fixos nas rotas na qual vamos usar esse `layout`;
- Para fazer o uso do `layout`, vamos no arquivo `AppRoutes.tsx` e agrupamos as rotas que vão possuir esse `layout`, deixando como no exemplo abaixo:
```tsx
<Routes>
	<Route path="/" element={<Layout />}>
		<Route path="/" index element={<Home />} />
		<Route path="/products" element={<Products />} />
	</Route>
</Routes>
```
