___
- Chamamos de tipagem *explícita*, quando declaramos o tipo da variável, como no exemplo abaixo:
```ts
let myName: string
```
- A inferência de tipos é quando o TypeScript deduz o tipo da variável baseado no valor que estamos atribuindo no momento que estamos declarando essa variável
```ts
let message = "Olá, tudo bem?"
```
- Desta maneira não conseguimos atribuir um valor de tipo diferente do valor dado no momento de sua declaração;