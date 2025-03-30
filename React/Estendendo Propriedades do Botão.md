___
- Podemos estender as propriedades de elementos HTML, para fazer isso podemos seguir o exemplo:
```tsx
type Props = React.ComponentProps<"button"> & {
	name: string
}

export function Button({ name, onClick }: Props) {
	return <button onClick={onClick}>{name}</button>
}
```
- Estamos reaproveitando as tipagens dos elementos HTML;
