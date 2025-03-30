___
- No *React*, fazemos de forma declarativa a nossa interface baseado em componentes.
- **Os componentes são funções**
```tsx
export function App(){
	return (
		<h1>Hello World</h1>
	)
}
```
- **Todo componente no seu nome deve começar com letra maiúscula**
- **Todo componente tem um retorno, e no retorno colocamos o conteúdo que queremos declarar, que deve ser renderizado na tela;
- Para usarmos um componente fazemos como no exemplo abaixo:
```tsx
// Componente App
<App />
```
- Agora para executar o nosso projeto, usamos o comando:
```zsh
npm run dev
```
