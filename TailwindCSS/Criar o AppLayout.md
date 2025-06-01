___
- Para criarmos o *layout* que vai ser compartilhado entre as rotas, dentro da pasta `pages`, vamos criar o arquivo `AppLayout.tsx`e dentro desse arquivo vamos fazer o seguinte:
```TSx
import { Outlet } from 'react-routes'

export function AppLayout() {
	return (
		<div className="w-screen h-screen bg-gray-400 flex flex-col items-center text-gray-100">
			<main className="p-3 md:w-auto">
				<Outlet />
			</main>
		</div>
	)
}
```
- Agora voltamos ao arquivo `EmployeeRoutes`e envolvemos nossas rotas pelo `AppLayout`ficando da seguinte maneira:
```tsx
import { Routes, Route } from 'react-router'

import { Refund } from '../pages/Refund'
import { NotFound } from '../pages/NotFound'

export function EmployeeRoutes() {
	return (
		<Routes>
			<Route path="/" element={<AppLayout />}>
				<Route path="/" element={<Refund />} />
			</Route>	
			
			<Route path="*" element={<NotFound /> } />
		</Routes>
	)
}
```