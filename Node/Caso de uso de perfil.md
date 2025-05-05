___
- Na pasta `useCases`, vamos criar o arquivo `getUserProfile.ts` e dentro dele vamos fazer o seguinte:
```ts
interface GetUserProfileUseCaseRequest {
	userId: string
}


interface GetUserProfileUseCaseResponse {
	user: User
}

export class GetUserProfileUseCase {
	constructor(private usersRepository: UsersRepository) {}

	async execute({userId}: GetUserProfileUseCaseRequest): Promise<GetUserProfileUseCaseResponse> {
		const user = await this.usersRepository.findById(userId)

		if(!user) {
			throw new ResourceNotFoundError()
		}

		return {
			user,
		}
	}
}
```
- Agora no nosso repositório criamos um novo método o `findById
```ts
export interface UsersRepository {
	findById(id: string) : Promise<User | null>
	findByEmail(email: string): Promise<User | null>
	create(data: Prisma.UserCreateInput): Promise<User>
	
}
```
- Como a verificação de usuário é bem recorrente, podemos criar um erro mais generico, para isso dentro da pasta `errors`, podemos criar o arquivo `ResourceNotFoundError.ts`e dentro dele seguimos as estruturas dos outros erros.
- Agora podemos criar o arquivos de testes desse caso de uso.
```ts
import { InMemoryUsersRepository } from '@/repositories/in-memory/in-memory-users-repository'
 import { ResourceNotFoundError } from '@/use-cases/errors/resource-not-found-error'
 import { GetUserProfileUseCase } from '@/use-cases/get-user-profile'
 import { hash } from 'bcryptjs'
 import { expect, describe, it, beforeEach } from 'vitest'
 
 let usersRepository: InMemoryUsersRepository
 let sut: GetUserProfileUseCase
 
 describe('Get User Profile Use Case', () => {
   beforeEach(() => {
     usersRepository = new InMemoryUsersRepository()
     sut = new GetUserProfileUseCase(usersRepository)
   })
 
   it('should be able to get user profile', async () => {
     const createdUser = await usersRepository.create({
       name: 'John Doe',
       email: 'johndoe@example.com',
       password_hash: await hash('123456', 6),
     })
 
     const { user } = await sut.execute({
       userId: createdUser.id,
     })
 
     expect(user.name).toEqual('John Doe')
   })
 
   it('should not be able to get user profile with wrong id', async () => {
     expect(() =>
       sut.execute({
         userId: 'non-existing-id',
       }),
     ).rejects.toBeInstanceOf(ResourceNotFoundError)
   })
 })
```
