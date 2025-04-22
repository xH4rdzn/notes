___
- Podemos definir os valores iniciais para os inputs controlados, para isso fazemos como no exemplo abaixo:
```tsx
import { Controller, useForm } from 'react-hook-form'

export function App() {
		const { control, handleSubmit } = useForm({ defaultValues: {
		name: ""
	}})

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