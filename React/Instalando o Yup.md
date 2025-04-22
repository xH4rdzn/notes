___
- Podemos validar os dados do nosso formulário, podemos usar varias bibliotecas, como o `zod`, mas nesse caso vamos usar o `yup`;
- Para instalar o `yup`, usamos o comando:
```zsh
npm i @hookform/resolvers yup
```
- Agora para fazer o uso dele, importamos o `yupResolver`:
```tsx
import { yupResolver } from '@hookform/resolvers/yup'
```
- E agora passamos para o nosso `useForm` o `resolver`, e nele atribuímos o `yup`
```tsx
const { control, handleSubmit } = useForm<FormData>({
		defaultValues: {
			name: "",
		},
		resolver: yupResolver()
	})
```
- Mas precisamos passar o `schema`de validação como parâmetro para ele;
- Deixando da seguinte maneira:
```tsx
import * as yup from 'yup'

const schema = yup.object({})

const { control, handleSubmit } = useForm<FormData>({
		defaultValues: {
			name: "",
		},
		resolver: yupResolver(schema)
	})
```