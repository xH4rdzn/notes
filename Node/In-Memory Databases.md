___
- Para não ficarmos criando em todos os testes o nosso *repositório fake*, vamos criar um arquivo para armazenar essas variáveis.
- Para isso dentro da pasta `repositories`, vamos criar uma pasta com o nome de `InMemory`, e dentro dessa pasta vamos criar o nossos *repositórios* que vão ser armazenados na memoria para realizarmos os testes.
- Nesse caso como estamos testando o `RegisterUseCase`vamos criar o arquivo `inMemoryUsersRepository.ts`e dentro dele vamos fazer o seguinte:
```ts
export class InMemoryUsersRepository implements UsersRepository {
	public items: User[] = []

	async findByEmail(email: string) {
		const user = this.items.find((item) => item.email === email)

		if(!user) {
			return null
		}

		return user	
	}

	async create(data: Prisma.UserCreateInput) {
		const user = {
			id: 'user-1',
			name: data.name,
			email: data.email,
			password: data.password,
			created_at: new Date()
		}

		this.items.push(user)

		return user
	}
}
```
- Agora voltamos ao nosso arquivo de testes e fazemos a seguinte alteração:
```ts
import { expect, describe, it } from 'vitest'
import { compare } from 'bcryptjs'
import { RegisterUseCase } from './register'

describe('Register Use Case', () => {
	it('should hash user password upon registration', () => {
		const usersRepository = new InMemoryUsersRepository() 
		const registerUseCase = new RegisterUseCase(usersRepository)
	

		const { user} = await registerUseCase.execute({
			name: 'John Doe',
			email: 'johndoe@email.com',
			password: '123456'
		})

		const isPasswordCorrectlyHashed = await compare('123456', user.password)

		expect(isPasswordCorrectlyHashed).toBe(true)
})
```
- Agora podemos reaproveitar esse repositório para realizar os outros testes, como por exemplo o teste de se cadastrar utilizando o mesmo email:
```ts
	it('should not be able register with same email twice', async () => {
		const usersRepository = new InMemoryUsersRepository()
		const registerUseCase = new RegisterUseCase(usersRepository)


		const email = 'johndoe@email.com'

		await registerUseCase.execute({
			name: 'John Doe',
			email,
			password: '123456',
		})

		await expect(() => 
			registerUseCase.execute({
				name: 'John Doe',
				email,
				password: '123456',
			}),
		).rejects.toBeInstanceOf(UserAlreadyExistsError)
	})
```
- E também podemos criar um teste para ver se já é possível se realizar:
```ts
it('should be able to register', async () => {
	const usersRepository = new InMemoryUsersRepository()
	const registerUseCase = new RegisterUseCase(usersRepository)

	const { user } = await registerUseCase.execute({
		name: 'John Doe',
		email: 'johndoe@email.com',
		password: '123456',
	})

	expect(user.id).toEqual(expect.any(String))
})
```
- Desta maneira finalizamos a primeira *switch* de testes da nossa aplicação.
