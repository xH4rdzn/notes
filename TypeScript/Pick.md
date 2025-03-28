___
- Usamos esse utilitário, para escolher qual é a propriedade que queremos reaproveitar de um tipo;
```ts
interface Book {
	title: string
	pages: number
	author: string
}

const book: Pick<Book, "title"> = { title: "TypeScript" }
```
- Com o `Pick`, conseguimos reaproveitar quantas propriedades quisermos, como demostrado no exemplo abaixo:
```ts
interface Book {
	title: string
	pages: number
	author: string
}

const book: Pick<Book, "title" | "pages"> = { title: "TypeScript", pages: 150 }
```
