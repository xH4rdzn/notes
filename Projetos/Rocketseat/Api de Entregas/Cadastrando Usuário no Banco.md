___
- Após fazermos o [[Criando o Prisma Database|arquivo prisma]] que realiza a conexão com o banco de dados, voltamos ao nosso `controller` de usuários e importamos esse arquivo
```ts
import { prisma } from "@/database/prisma"
```
- E no método `create`, logo após a validação dos dados do usuário, podemos fazer a verificação se existe um usuário com o mesmo endereço de e-mail já cadastrado.
```ts
const userWithSameEmail = await prisma.users.findFirst({ where: { email}})

if(userWithSameEmail) {
	throw new AppError("User with same email already exists")
}
```
- Se não lançar uma exceção significa que não existe nenhum usuário com esse e-mail cadastrado, então fazemos o [[Criptografando Senha do Usuário|hash]] da senha e inserimos esse usuário no banco de dados da seguinte maneira:
```ts
const user = await prisma.user.create({
	data: {
		name,
		email,
		password: hashedPassword,
	}
})
```
- E podemos fazer o retorno desse usuário
```ts
return response.json(user)
```
- Mas ele devolve todos os dados, e não queremos que ele devolva a `password`e nem a `role`, para resolver isso desestruturamos de dentro do usuário a senha, como no exemplo abaixo:
```ts
const { password: _, ...userWithoutPassword } = user
```
- E agora devolvemos a variável `userWithoutPassword`
```ts
return response.status(201).json(userWithoutPassword)
```
*Desta maneira, mesmo que a senha esteja criptografada, preservamos a senha do nosso usuário;*
