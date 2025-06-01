___
- Quando acessamos uma rota aleatória, a nossa tela fica toda em branco.
- O *ideal* seria ele ir para um página dizendo onde não existe ou não foi encontrado nenhuma rota naquele endereço.
- Para isso dentro da pasta `pages`, vamos criar o arquivo `NotFound.tsx`e dentro desse arquivo vamos fazer o seguinte:
```Tsx
export function NotFound() {
	return (
		<div>
			<h1>Ops! Essa página não existe</h1>
			<a href="/">Voltar para o inicio</a>
		</div>
	)
}
```
- Agora no nosso arquivo de *rotas*, no caso o `AuthRoutes`e vamos adicionar:
```tsx
export function AuthRoutes() {
	return (
		<Routes>
			<Route path="/" element={}>
				<Route path="/" element={<SignIn />} />
				<Route path="/signup" element={<SignUp />} />
			</Route>

			<Route path="*" element={<NotFound />} />
		</Routes>
	)
}
```
- Agora voltamos ao arquivo `NotFound.tsx`e estilizamos ele utilizando as classes do **TailwindCSS**
