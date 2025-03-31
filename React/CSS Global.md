___
- É muito comum criarmos um arquivo css de configuração para resetar as configurações do navegador e configurações globais em nossa aplicação;
- Geralmente damos o nome de `global.css`;
- Dentro da pasta `src`, criamos o arquivo `global.css`;
- Dentro dele definimos as configurações globais:
```css
* {
	margin: 0;
	padding: 0;
}

body {
	background-color: #121213;
}
```
- E agora importamos esse arquivo no topo do arquivo `App.tsx`
```tsx
import './global.css'
```