___
- Uma coisa que podemos fazer com um middleware, é modificar o conteúdo da requisição.
- Podemos adicionar propriedades para a nossa requisição, e para isso precisamos modificar a tipagem da requisição.
- Então para fazermos isso vamos:
1. Criar uma pasta `types`, dentro da pasta `src`
2. Dentro da pasta `types`, vamos criar um arquivo com o nome de: `request.d.ts`
3. Dentro desse arquivo, vamos fazer a seguinte alteração:
```ts
declare namespace Express {
	export interface Request {
		user_id: string
	}
}
```
- Podemos adicionar quantas propriedades precisarmos.
- Agora podemos usar essa propriedade, na requisição que usa esse middleware