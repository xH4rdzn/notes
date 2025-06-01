___
- Agora que terminamos as rotas de login e criação de conta, vamos criar as novas rotas.
- Dentro da pasta `pages`, vamos criar o arquivo com o nome `Refund.tsx`e dentro desse arquivo inicialmente vamos apenas retornar um `h1`
```tsx
export function Refund() {
	return <h1>Refund</h1>
}
```
- Agora dentro da pasta `routes`, vamos criar o arquivo `EmployeeRoutes.tsx` e dentro desse arquivo vamos fazer o seguinte:
```TSx
import { Routes, Route } from 'react-router'

import { Refund } from '../pages/Refund'
import { NotFound } from '../pages/NotFound'

export function EmployeeRoutes() {
	return (
		<Routes>
			<Route path="/" element={<Refund />} />
			<Route path="*" element={<NotFound /> } />
		</Routes>
	)
}
```
- Agora voltamos ao arquivo `index.tsx` importamos o arquivo `EmployeeRoutes.tsx`e trocamos com o componente `AuthRoutes`, apenas para realizarmos testes e estilizar essa parte, depois deixaremos de maneira dinâmica.