___
- Para instalar o Tailwind em nosso projeto que estamos `vite`, podemos instalar usando o comando:
```zsh
npm install tailwindcss @tailwindcss/vite
```
-  Após isso vamos no arquivo `vite.config.ts`e adicionamos o plugin do `tailwind`
```ts
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
	plugins: [
		tailwindcss(),
		react()
	]
})
```
- Agora no nosso arquivo principal de css, temos que fazer a importação do tailwindcss
```css
@import "tailwindcss";
```
- Desta maneira já temos o tailwindcss instalado em nossa aplicação;