___
- Para alterar o título da página e o favicon, vamos no arquivo `index.html`e lá fazemos essas alterações
- Para usar os itens que estão na pasta pública podemos fazer como no exemplo abaixo:
```HTML
<link rel="icon" type="image/svg+xml" href="/favicon.svg" />
```
- No arquivo `index.html`, também podemos fazer a importação de fontes personalizadas
- Agora vamos adicionar o *css global*, criando o arquivo `global.css`
```css
:root {
	font-size: 16px;
}

* {
	padding: 0;
	margin: 0;
	box-sizing: border-box;
}

body {
	background-color: #F5F5FA;
	font-family: "Noto Sans", serif;
	font-optical-sizing: auto;

}

button {
	cursor: pointer;
	transition: filter 0.2s;
}

button:hover {
	filter: brightness(0.9);
}
```
- E agora fazemos a importação desse arquivo no arquivo `main.tsx`
```tsx
import './global.css'
```