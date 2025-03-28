___
- Aprendemos como [[Conhecendo interface no Typescript|criar uma interface]], agora vamos aprender como estender essa interface para receber outras interface, como no exemplo abaixo:
```ts
interface Teacher {
	id: number,
	name: string,
	subjects: string[]
}

interface Student {
	id: number,
	name: string,
	age: number,
}
```
- Como podemos notar, temos as propriedades `id`e `name`repetidas nas duas interfaces, mas podemos estender essas interfaces para não repetir essas propriedades:
```ts
interface Person {
	id: number,
	name: string,
}

interface Teacher extends Person {
	subjects: string[]
}

interface Student extends Person {
	age: number,
}
```