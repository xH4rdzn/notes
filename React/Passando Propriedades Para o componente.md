___
- Já [[Criando um componente|criamos um componente]] e já estamos utilizando ele;
- Mas todos esses componentes estão com informações fixas, mas utilizando propriedades, conseguimos deixar essas propriedades dinâmicas;
- Para passar uma propriedade podemos fazer da seguinte maneira:
```tsx
//
export function App() {
	return (
		<div>
			<Button name="Criar"/> // Passando uma propriedade
			<Button />
		</div>
	)
}
```
- Agora no arquivo do nosso componente para recuperar essa propriedade, podemos fazer da seguinte maneira:
```tsx
export function Button(props) {
	return <button>{props.nomeDaPropriedade}</button>
}
```
- Podemos tipar o conteúdo das propriedades, como no exemplo abaixo:
```tsx
type Props = {
	name: string
}
```
- E agora passamos para a função do componente da seguinte maneira:
```tsx
export function Button(props: Props) {
	return <button>{props.nomeDaPropriedade}</button>
}
```
- *Nota-se que para conteúdo dinâmico, precisamos passar entre `{ }`*
- Podemos fazer a desestruturação dessas propriedades, para isso fazemos o seguinte:
```tsx
export function Button({name }: Props) {
	return <button>{name}</button>
}
```
- *Nota-se que fazendo a desestruturação, podemos colocar diretamente entre `{ }`o nome da propriedade que passamos.*