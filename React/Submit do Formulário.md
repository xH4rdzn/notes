___
- Toda vez que temos um `button`, do tipo *submit* dentro de um formulário, ele irá fazer um refresh, perdendo todos os dados do formulário, mas podemos evitar isso, para isso seguimos o exemplo:
```Tsx
import { useState } from 'react'

export function App() {
	const [name, setName] = useState("")

	function onSubmit(e: React.FormEvent<HTMLElement>) {
		e.preventDefault()
	}

	return (
		<form>
			<input 
				type="text"
				placeholder="Nome do evento"
				onChange={(e) => setName(e.target.value)}
			/>

			<button 
				type="submit"
				onClick={onSubmit}
			>
				Salvar
			</button>
		</form>
	)
}
```
- Mas podemos fazer de outra maneira como demostrado no exemplo abaixo:
```Tsx
import { useState } from 'react'

export function App() {
	const [name, setName] = useState("")

	function onSubmit(e: React.FormEvent<HTMLElement>) {
		e.preventDefault()
	}

	return (
		<form onSubmit={onSubmit}>
			<input 
				type="text"
				placeholder="Nome do evento"
				onChange={(e) => setName(e.target.value)}
			/>

			<button type="submit">
				Salvar
			</button>
		</form>
	)
}
```