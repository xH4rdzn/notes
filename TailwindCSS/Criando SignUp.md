___
- Vamos criar a tela de `SignUp`, olhando o *figma do projeto*, temos a mesma estrutura o que muda são os campos, então podemos copiar o mesmo código da tela de `SignIn`;
- E no arquivo `AuthRoutes.tsx`, disponibilizamos essa nova rota.
```tsx
import { Routes, Route } from 'react-router'
import { AuthLayout } from '../components/AuthLayout'
import { SignIn } from '../pages/SignIn'
import { SignUp } from '../pages/SignUp'

export function AuthRoutes() {
	return (
		<Routes>
				<Route path="/" element={<AuthLayout/>}>
				<Route path="/" element={<SignIn />} />
				<Route path="/signin" element={<SignUp/>} />
			</Route>
		</Routes>
	)
}
```
- Já no arquivo `SignUp`, fazemos as modificações necessárias.
