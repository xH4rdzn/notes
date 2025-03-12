___
- Operador lógico que retorna o seu operando do lado direito quando o seu operador do lado esquerdo é `null`ou `undefined`. Caso contrário, ele retorna o seu operando do lado esquerdo.
```js
let content = null
console.log(content ?? "Conteúdo padrão") // Retorna o "Conteúdo padrão"
```
- Como o lado esquerdo é `null`, ele exibe o conteúdo do lado direito
- Se não fosse `null`, iria aparecer o conteúdo da variável `null`;
- Tem esse comportamento com `null`ou `undefined`;
