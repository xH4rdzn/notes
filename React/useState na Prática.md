___
- Para podermos usar o `useState`, precisamos importar, normalmente importamos o mais no topo possível, como no exemplo abaixo:
```tsx
import { useState } from 'react'
```
- E agora para utilizar esse hook, usamos dentro do nosso componente:
```tsx
import { useState } from 'react'

export function App() {
	const [count, setCount] = useState(0)
}
```
- A primeira posição é o estado em si, podemos dar o nome que quisermos;
- A segunda posição é a função que atualiza o estado, sempre a função que atualizar o estado recebe o prefixo de `set`
- Para utilizar essa função para modificar o estado podemos fazer como no exemplo abaixo:
```tsx
import { useState } from 'react'

export function App() {
	const [count, setCount] = useState(0)

	return (
		<div>
			<Button name="Adicionar" onClick={() => setCount(count + 1)}/>
			<span>{count}</span>
			<Button name="Remover" onClick={() => setCount(count - 1)} />
		</div>
	)
}
```
- Podemos criar funções que acionam a função de alterar o estado, como no exemplo abaixo:
```tsx
import { useState } from 'react'

export function App() {
	const [count, setCount] = useState(0)

	function handleAdd(){
		setCount(count + 1)
	}

	function handleRemove(){
		setCount(count -1)
	}

	return (
		<div>
			<Button name="Adicionar" onClick={handleAdd}/>
			<span>{count}</span>
			<Button name="Remover" onClick={handleRemove} />
		</div>
	)
}
```
- Desta maneira não precisamos passar a notação de `Arrow Function`, mas apenas função que dispara a atualização de estado.