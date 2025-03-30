___
- Para habilitar o *CORS*, primeiramente precisamos instalar ele, para isso vamos utilizar o comando:
```zsh
npm i cors@2.8.5
```
- E agora precisamos instalar as tipagens dele:
```zsh
npm i @types/cors@2.8.17 -D
```
- Agora dentro do arquivo `app.ts`, adicionamos o seguinte código:
```ts
import cors from 'cors'


// após a instancia do express
app.use(cors())
```