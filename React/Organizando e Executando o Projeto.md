___
- Dentro da pasta `src`, vamos apagar:
	- A pasta *assets*
	- O `app.css`;
	- Dentro do `app.tsx`, vamos apagar tudo e adicionar:
```tsx
export default function App() {
	return <h1>Hello World</h1>
}
```
- Vamos apagar o arquivo `index.css`;
- Vamos criar o arquivo `main.css`e dentro dele vamos fazer o seguinte:
```css
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

body {
	width: 100%;
	height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
	background-color: #fbf4f4;
}

h1 {
	margin: 22px 0;
}
```
- Dentro do arquivo `main.tsx`, trocamos a importação do CSS para o arquivo que criamos anteriormente;
- Apagamos o arquivo `eslint.config.js`.
- Apagamos o `README.MD`
- Dentro do `package.json`, apagamos todas as dependências que estão relacionadas ao `eslint`
- Agora executamos o comando:
```zsh
npm i
```
- E agora podemos rodar o nosso projeto com o comando:
```zsh
npm run dev
```
