___
- Para podermos usar o `useEffect`, precisamos importar
```tsx
import { useEffect } from 'react'
```
- Normalmente colocamos o `useEffect`, perto do `return`
```tsx
import { useState, useEffect } from 'react'

export function App() {
	const [count, setCount] = useState(0)

	function handleAdd(){
		setCount(count + 1)
	}

	function handleRemove(){
		setCount(count -1)
	}

	useEffect(() => {
		console.log('Bem-vindo')
	}, [])

	return (
		<div>
			<Button name="Adicionar" onClick={handleAdd}/>
			<span>{count}</span>
			<Button name="Remover" onClick={handleRemove} />
		</div>
	)
}
```
- Conseguimos usar o `useEffect`, dentro de componentes e outros hooks, sendo assim ele executando em diferentes contextos;
- Se passarmos alguma variável de estado, como dependência do `useEffect`toda vez que esse estado sofrer alguma alteração, a lógica do `useEffect`será executada;
```tsx
import { useState, useEffect } from 'react'

export function App() {
	const [count, setCount] = useState(0)

	function handleAdd(){
		setCount(count + 1)
	}

	function handleRemove(){
		setCount(count -1)
	}

	useEffect(() => {
		console.log('O valor mudou!')
	}, [count])

	return (
		<div>
			<Button name="Adicionar" onClick={handleAdd}/>
			<span>{count}</span>
			<Button name="Remover" onClick={handleRemove} />
		</div>
	)
}
```