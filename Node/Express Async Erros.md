___
- Vamos utilizar uma outra biblioteca, vamos instalar ela com o comando:
```zsh
npm i express-async-errors
```
- Essa biblioteca vai facilitar o tratamento de erros.
- Para usarmos seguimos os passos abaixo:
1. Após instalar com o comando acima importamos o arquivo no arquivo do `server.ts`, como no exemplo abaixo:
```ts
import "express-async-errors"
```
2. Agora não precisamos mais usar o `next: NextFunction` e nem o `try/catch`, ele vai fazer de maneira automática; 