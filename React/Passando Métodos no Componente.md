___
- Já aprendemos a passar [[Passando Propriedades Para o componente|propriedades para um componente]], mas também podemos passar um método para esse componente;
- Para fazer a tipagem podemos seguir o exemplo:
```tsx
type Props = {
	name: string
	onClick: () => void
}
```
- Então agora podemos recuperar esse método dentro do componente:
```tsx
type Props = {
	name: string
	onClick: () => void
}

export function Button({ name, onClick }: Props) {
	return <button onClick={onClick}>{name}</button>
}
```
- Agora para executar esse método, onde o componente é usado fazemos da seguinte maneira:
```tsx
export function App(){
	return (
		<div>
			<Button name="Criar" onClick={() => alert("Criar")}/>
			<Button name="Editar" onClick={() => alert("Editar")}/>
		</div>
	)
}
```


