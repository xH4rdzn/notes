___
- Agora que já instalamos o [[Conhecendo o React Hook Form|React Hook Form]], vamos adicionar as seguintes importações:
```tsx
import { Controller, useForm } from 'react-hook-form'
```
- Agora usamos da seguinte maneira:
```tsx
import { Controller, useForm } from 'react-hook-form'

export function App() {
	const { control, handleSubmit } = useForm()

	function onSubmit(data) {
		console.log(data)
	}

	return (
		<form onSubmit={handleSubmit(onSubmit)}>
			<Controller 
				control={control}
				name="name"
				render={({ field }) => (
					<input type="text" placeholder="Nome do evento" {...field}/>
				)}
			/>
			<input 
				type="text"
				placeholder="Nome do evento"
			/>

			<button type="submit">
				Salvar
			</button>
		</form>
	)
}
```