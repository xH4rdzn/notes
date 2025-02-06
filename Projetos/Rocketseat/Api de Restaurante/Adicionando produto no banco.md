___
- Para cadastrar o produto no banco de dados agora vamos utilizar o arquivo `knex`que criamos, para isso precisamos importar ele em nosso controller:
```ts
import { knex } from "@/database/knex"
```
- Agora após fazer a [[Validando dados do Produto|validação dos dados do produto]], adicionamos:
```ts
await knex("products").insert({
	
})
```
- Porém, como não temos a tipagem, podemos inserir qualquer dado, para evitar isso vamos adicionar as tipagens;
- Então dentro da pasta `database`, criamos a pasta `types` e dentro da pasta `types`criamos o arquivo `productRepository.d.ts`
![[Pasted image 20250205150444.png]]
- E dentro desse arquivo adicionamos o seguinte código:
```ts
type ProductRepository = {
	id: number
	name: string
	price: number
	created_at: number
	updated_at: number
}
```
- Agora voltamos ao `controller`e adicionamos essa tipagem, passando o que chamamos de `generic`da seguinte maneira:
```Ts
await knex<ProductRepository>("products").insert({
	name,
	price,
})
```
- Agora ele reclama se passarmos algo que não tem na tipagem.