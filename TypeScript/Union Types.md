___
- Até agora aprendemos a definir apenas um tipo para uma variável com o Typescript
```ts
let response: string
```
- Mas pode ter cenários que uma variável pode ter mais de um tipo;
- Para definirmos dois tipos ou mais em uma variável, que nós chamamos de `Union Types`, o fazemos utilizando o *pipe* (`|`)
```ts
let response: string | null | number
```
