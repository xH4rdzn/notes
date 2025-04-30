___
- Dentro da pasta `components`, vamos criar o arquivo `Input.tsx`, que será o nosso componente de input.
- Dentro dele vamos fazer o seguinte código:
```tsx
type Props = React.ComponentProps<"input"> & {
	legend?: string
}

export function Input({ legend, type = "text" , ...rest}: Props) {
	return (
		<fieldset>
			{
				legend &&
				<legend>
					{legend}
				</legend>
			}

			<input type={type} {...rest}/>
		</fieldset>
	)
}
```
- Agora podemos usar esse *Input*, na nossa página de `SignIn`;
- E com o tailwind, podemos estilizar o nosso input;