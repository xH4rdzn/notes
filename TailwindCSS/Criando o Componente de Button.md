___
- Agora vamos criar o componente de botão, para isso dentro da pasta `components`, vamos criar o arquivo `Button.tsx`;
- E dentro dele  vamos fazer o seguinte: 
```tsx
type Props = React.ComponentProps<"button"> & {
	isLoading?: boolean
}

export function Button({ children, isLoading, type = "button" }: Props) {
	return (
		<button type={type} disabled={isLoading} {...rest}>
			{children}
		</button>
	)
}
```
