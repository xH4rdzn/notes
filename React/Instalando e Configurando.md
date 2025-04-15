___
- Para instalar o `react-router`em nossa aplicação vamos usar o comando:
```zsh
npm i react-router
```
- Nos exemplos da aula vamos usar a versão `7.0.2`
```zsh
npm i react-router@7.0.2
```
- Agora no arquivo `main.tsx`, adicionamos as linhas abaixo:
```tsx
import { BrowserRouter } from 'react-router'


// Envolvemos o App pelo BrowserRouter
<BrowserRouter>
	<App />
</BrowserRouter>
```