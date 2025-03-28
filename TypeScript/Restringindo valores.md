___
- Podemos restringir valores que uma variável pode receber, como no exemplo abaixo:
```ts
type Size = "small" | "meidum" | "large"

let size: Size

size = "small"
```
- Com essa estratégia conseguimos restringir os valores que uma variável pode receber;