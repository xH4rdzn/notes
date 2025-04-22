___
- O método `onChange`, fica observando e toda vez que o conteúdo do input muda, conseguimos capturar o conteúdo atual do input
```tsx
<input 
	type="text"
	placeholder="Nome do evento" 
	onChange={e => console.log(e.target.value)}
/>
```
- Agora podemos guardar esse conteúdo em um lugar que podemos recuperar esses dados que vem do formulário, para isso podemos utilizar os estados
```tsx
import { useState } from 'react'

// Criando o estado
const [name, setName] = useState("")

export function App() {
	return (
		<input 
			type="text"
			placeholder="Nome do evento" 
			onChange={e => setName(e.target.value)}
		/>
	)
}

```
