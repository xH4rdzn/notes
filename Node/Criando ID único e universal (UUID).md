___
- Ao criarmos novos usuários, notamos que todos estão sendo salvos com o ***ID*** igual.
- Mas com o *Node*, conseguimos gerar um ***ID*** único.
- Para fazer isso precisamos fazer a importação da função `randomUUID`do módulo `crypto`
```js
import { randomUUID } from 'node:crypto'
```
- E agora onde estamos salvando o usuário, passamos essa função:
```js
const user = {
	id: randomUUID(),
	name,
	email,
}
```