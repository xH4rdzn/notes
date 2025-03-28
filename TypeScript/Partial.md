___
- O `Partial`é usado para tornar propriedades de uma `interface` opcionais;
- Ele também permite reaproveitar a tipagem existente, tornando propriedades selecionadas opcionais;
```ts
interface User {
	id: number,
	name: string,
	email: string
}

const newUser: User = {
	id: 1,
	name: "Igor",
	email: "igor@email.com"
}


// Usando o Partial, e deixando todas as propriedades de um tipo opcional;
const updatedUser: Partial<User> = {
	name: "Igor Coelho"
}
```
