___
- Agora vamos criar a nossa primeira rota;
- Para isso dentro da pasta `src`, vamos criar uma nova pasta, que vamos chamar de `pages`, essa pasta vai armazenar as nossas páginas;
- Agora vamos criar a página inicial da nossa aplicação, na qual vamos chamar de `home`, para isso criamos o arquivo `Home.tsx`e dentro desse arquivo adicionamos:
```tsx
export function Home(){
	return (
		<div>
			<h1>Página Home</h1>
		</div>
	)
}
```
- Agora dentro da pasta `src`, vamos criar outra pasta, na qual vamos chamar de `routes` e dentro dessa pasta, vamos criar o arquivo `AppRoutes.tsx`e dentro desse arquivo vamos fazer o seguinte:
```tsx
import { Routes, Route } from 'react-router'
import { Home } from '../pages/Home'

export function AppRoutes() {
	return (
		<Routes>
			<Route path="/" index element={<Home />}/>
		</Routes>
	)
}
```
- Agora voltamos ao arquivo `main.tsx`, e trocamos o `<App />`, pelo arquivo que criamos acima:
```tsx
import { AppRoutes } from './routes/AppRoutes'

<BrowserRouter>
	<AppRoutes />
</BrowserRouter>
```