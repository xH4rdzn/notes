___
- Na pasta `src`, podemos criar o arquivo de estilização, neste exemplo vamos criar o arquivo `styles.css`e dentro desse arquivo vamos adicionar a seguinte regra:
```css
.container {
	background-color: red;
}
```
- E agora onde queremos usar esse arquivo precisamos fazer a importação, que podemos fazer da maneira abaixo:
```tsx
import './styles.css'
```
- E agora para usar as classes, usamos o `className`, podemos fazer como no exemplo abaixo:
```tsx
export function App() {
	return (
		<div className="container">
			<Button name="Criar" onClick={() => alert("Criar")}/>
		</div>
	)
}
```
