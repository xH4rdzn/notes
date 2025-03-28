___
- Asserção de tipos é um recurso do typescript para utilizar quando ele não sabe a tipagem de um determinado objeto, e no dizemos que a tipagem é aquela que informamos, como no exemplo abaixo:
```ts
type UserResponse = {
	id: number,
	name: string,
	avatar: string
}

let userResponse = {} as UserResponse
```
- Nota-se que usamos o `as`, para fazer à asserção de tipos;