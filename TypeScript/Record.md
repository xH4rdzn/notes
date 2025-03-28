___
- O utilitário `Record`, nos permite fazer o mapeamento do tipo de um objeto para outro;
- É muito usado para definir a tipagem de objetos;
```ts
// O primeiro valor é para as chaves
// O segundo valor é para o valor

// Record<Tipochave, Tipovalor>
const scores: Record<string, number> = {
	// Podemos usar assim
	"Igor": 10
	// ou assim
	Rodrigo: 10
}
```
- Podemos usar o `Record`, para limitar valores, para fazer isso podemos seguir o exemplo abaixo:
```ts
type Profile = "admin" | "user" | "guest"

// Limitando as chaves de um objeto
const user: Record<Profile, number> = {}
```
- Da maneira acima só conseguimos usar as chaves que foram definidas no `type Profile`;
- Podemos também dar valor personalizados
```ts
interface User {
	name: string
	email: string
}
const users: Record<number, User> = {
	1: {name: "Igor", email: "igor@email.com"},
	2: {name: "Lucas", email: "lucas@email.com"}
}
```

