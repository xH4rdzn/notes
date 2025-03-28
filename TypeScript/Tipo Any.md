___
- O tipo *any* é um tipo especial do *Typescript*, e ele é automaticamente inferido, quando só declaramos e não atribuímos um valor para uma variável
```ts
let message
```
- Também podemos inferir o tipo *any* de maneira explicita
```ts
let message: any
```
- Com o tipo *any*, a variável aceita qualquer valor.
- Geralmente usamos o *any*, quando não temos certeza do tipo de valor que a variável vai receber;
- Devemos tomar cuidado ao utilizar o *any*;
