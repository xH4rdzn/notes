___
- Quando uma expressão tem múltiplos operadores, na programação e em expressões matemáticas, a ordem de precedência *define qual operação será realizada primeiro.*
- O primeiro calculo a ser efetuado em uma expressão sem o [[Grouping Operator]] é a **exponenciação** `**`
- Depois multiplicação e divisão: `*`, `/,//, %`;
- Depois adição e subtração: ` +, -`;
- Os operadores relacionais: `==, !=, <=, >=, >, <`;
- E depois os operadores lógicos na sequencia: `not, and, or`
```js
2 + 3 * 4 = 14
```
- Porém com [[Grouping Operator]], ele muda a ordem, sendo assim o operador vem primeiro na *ordem de precedência*
```js
( 2 + 3 ) * 4 = 20
```