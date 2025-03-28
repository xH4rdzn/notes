___
- O `Omit`, pode ser usado para reaproveitar tipagens omitindo propriedades;
```ts
interface Book {
	title: string
	pages: number
	author: string
	description: string
}

// Usando o Omit
const book: Omit<Book, "description"> = {
	title: "TypeScript",
	pages: 100,
	author: "Igor"
}
```
- Podemos omitir, mais de uma propriedade, para isso fazemos da seguinte maneira:
```ts
interface Book {
	title: string
	pages: number
	author: string
	description: string
}

// Usando o Omit com mais de uma propriedade
const book: Omit<Book, "description" | "pages"> = {
	title: "TypeScript",
	author: "Igor"
}
```