___
- Como vamos usar o `express`, precisamos instalar ele, então usamos o comando:
```bash
npm i express
```
- Agora podemos usar o `express`, vamos no arquivo `server.ts` e importamos o `express`, da seguinte maneira:
```ts
import express from "express"
```
- Porém vai dar uma espécie de erro, e para resolver precisamos instalar as tipagens do `express`, com o comando:
```bash
npm i --save-dev @types/express
```