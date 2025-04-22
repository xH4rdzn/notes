___
- Podemos definir a tipagem desse formulário, para isso podemos criar um tipo e passar, da seguinte maneira:
```tsx
type FormData = {
	name: string
}

import { Controller, useForm } from 'react-hook-form'

export function App() {
	const { control, handleSubmit } = useForm<FormData>({
		defaultValues: {
			name: "",
		},
	})

	function onSubmit(data: FormData) {
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