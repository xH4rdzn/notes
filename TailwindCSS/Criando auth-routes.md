___
- Agora vamos criar as rotas de `auth` para isso dentro da pasta `src`, vamos criar a pasta `pages`, essa pasta vai ser onde vamos por as nossas páginas;
- E vamos criar o componente `SignIn`:
```tsx
export function SignIn() {
	return <h1>SignIn</h1>
}
```
- E agora precisamos instalar o `react-router`, para isso vamos usar o comando:
```zsh
npm i react-router
```
- Agora dentro da pasta `src`, vamos criar uma pasta `routes`;
- Dentro dessa pasta vamos criar o arquivo `authRoutes.tsx`, e dentro desse arquivo vamos fazer o seguinte:
```tsx
import { Routes, Route } from 'react-router'

import { SignIn } from '../pages/SignIn'

export function AuthRoutes() {
	return (
		<Routes>
			<Route path="/" element={<SignIn />} />
		</Routes>
	)
}
```
- Agora dentro da pasta `routes`, vamos criar o arquivo `index.tsx`e vamos fazer o seguinte:
```tsx
import { BrowserRouter } from 'react-router'
import { AuthRoutes } from './authRoutes'

export function Routes() {
	return (
		<BrowserRouter>
			<AuthRoutes />
		</BrowserRouter>
	)
}
```
- Agora vamos no arquivo `App.tsx` e alteramos para a seguinte estrutura:
```tsx
import { Routes } from './routes'

export function App() {
	return <Routes />
}
```
