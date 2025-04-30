___
- Dentro de `src`, vamos criar uma pasta com o nome de `components`;
- Dentro dessa pasta vamos criar o arquivo `AuthLayout.tsx`e dentro dele vamos fazer o seguinte:
```tsx
import { Outlet } from 'react-router'

import logoSvg from '../assets/logo.svg'

export function AuthLayout() {
	return (
		<div>
			<main>
				<img src={logoSvg} alt="logo" />
				<Outlet />
			</main>
		</div>
	)
}
```
- Agora para usar o `AuthLayout`, vamos no arquivo `authRoutes`e o utilizamos da seguinte maneira:
```tsx
import { Routes, Route } from 'react-router'
import { AuthLayout } from '../components/AuthLayout'
import { SignIn } from '../pages/SignIn'

export function AuthRoutes() {
	return (
		<Routes>
			<Route path="/" element={<AuthLayout />}>
				<Route path="/" element={<SignIn />} />
			</Route>
		</Routes>
	)
}
```
- Agora podemos estilizar o `AuthLayout`, utilizando as classes do tailwind:
	- `w-screen`-> pegar toda a largura da tela;
	- `h-screen`-> pegar toda a altura da tela;
	- `flex`-> ativar o flexbox
	- `flex-col` -> altera o *flex-direction* para *column*
	- `justify-center` -> Para centralizar verticalmente
	- `items-center`-> Para centralizar horizontalmente
	- `p-8`-> padding de 32px;
	- `rounded-md`-> border-radius;