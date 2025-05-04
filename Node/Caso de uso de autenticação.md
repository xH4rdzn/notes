___
- Sempre vamos começar pelo `service`ou `useCase`;
- Então na pasta `useCases`, vamos criar um arquivo com o nome `authenticate.ts`e dentro dela vamos fazer o seguinte:
```ts
import { UsersRepository } from '@/repositories/usersRepository'


interface AuthenticateUseCaseRequest{
	email: string
	password: string
}

interface AuthenticateUseCaseResponse{
	user: User
}

export class AuthenticateUseCase {
	constructor(private usersRepository: UsersRepository) {}

	async execute({email, password}: AuthenticateUseCaseRequest): Promise<AuthenticateUseResponse> {
		const user = await this.usersRepository.findByEmail(email)

		if(!user) {
			throw new InvalidCredentialsError()
		}

		const doesPasswordMatches = await compare(password, user.password)

		if(!doesPasswordMatches) {
			throw new InvalidCredentialsError()
		}

		return {
			user,
		}
	}
}
```
- Para tratar o error, dentro da pasta `erros`, vamos criar o erro do tipo: `invalidCredentialsError.ts`e dentro dele vamos fazer o seguinte:
```ts
export class InvalidCredentialsError extends Error {
	constructor() {
		super('Invalid Credentials')
	}
}
```
- Agora que nosso caso de uso já esta pronto, vamos escrever os testes.
