___
- Para navegar até a rota que disponibilizamos, podemos usar a *tag* `a`, do HTML;
- Fazendo como no exemplo abaixo:
```tsx
export function Home(){
	return (
		<div>
			<h1>Página Home</h1>

			<nav>
				<a href="/products">Produtos</a>
			</nav>
		
		</div>
	)
}
```
- Agora temos um link, que vai apontar para rota de produtos;
- Para criar um link para voltar, podemos usar a mesma estrutura, porém colocamos o `href`, com um `/`, que normalmente seria a página inical;