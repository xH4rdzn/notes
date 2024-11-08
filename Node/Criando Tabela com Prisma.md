___
- No arquivo `schema.prisma`, é onde criamos as nossas tabelas;
- Para criar uma tabela usamos a keyword `model`, como no exemplo a seguir:
```prisma
model User {
	id String @id @default(uuid())
	name String
	email String @unique

	@@map("users")
}
```
- `@id` -> indica que essa coluna é a chave primária;
- `@default()` -> determinar o valor padrão do campo
- `uuid()` -> gera um uuid de maneira automática;
- `@unique` -> O campo com essa anotação, torna-se único, não se pode ter outro na mesma tabela;
- `@@map()` -> Definimos o nome da tabela que queremos no banco de dados ;
- Após criarmos a nossa tabela com o que queremos, precisamos criar uma `migration`, para isso usamos o comando abaixo:
```zsh
npx prisma migrate dev
```
- Após rodar o comando acima, precisamos dar um nome para a `migration`