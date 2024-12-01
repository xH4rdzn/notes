___
- Agora que já [[Validando Dados do Usuário]], precisamos criptografar a senha dele;
- Para isso vamos instalar a biblioteca `bcrypt`, com o comando:
```zsh
npm i bcrypt
```
- Como estamos usando o `typescript`, precisamos também instalar suas tipagens, para isso usamos o comando:
```zsh
npm i @types/bcrypt -D
```
- Agora, em nosso `controller` de usuários precisamos importar o `hash` do `bcrypt`
```ts
import { hash } from "bcrypt"
```
- E após a validação dos dados do usuário, podemos fazer a criptografia da seguinte maneira:
```ts
const hashedPassword = await hash(password, 8)
```
*Como estamos usando o `await`, o nosso método precisa receber `async`*
```ts
async create(request: Request, response: Response){}
```