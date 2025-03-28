___
- Podemos fazer a *intersecção de tipos*, como uma estratégia para estender o `type`, como no exemplo a seguir:
```ts
type Person = {
	id: number,
	name: string
}

type Teacher = Person & {
	subjects: string[]
}

type Student = Person & {
	age: number
}
```