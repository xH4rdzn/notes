___
- Podemos fazer da seguinte maneira também:
```tsx
type Props = React.ComponentProps<"button"> & {
	name: string
}

export function Button({ name, ...rest}: Props) {
	return <button {...rest}>{name}</button>
}
```
- Desta maneira conseguimos pegar todas as propriedades de uma vez e fazer sua utilização;
