____
- Agora vamos criar o caso de uso do *check-in*, para isso dentro da pasta `useCases`, vamos criar o arquivo `checkIn.ts`
```ts
interface CheckInUseCaseRequest {
	userId: string
	gymId: string
}

interface CheckInUseCaseResponse {
	checkIn: CheckIn
}


export class CheckInUseCase {
	constructor(private checkInsRepository: CheckInsRepository) {}

	async execute({
		userId,
		gymId,
	}: CheckInUseCaseResponse): Promise<CheckInUseCaseResponse> {
		const checkIn = await this.checkInsRepository.create({
			gym_id: gymId,
			user_id: userId,
		})

		return {
			checkIn,
		}
	}
}
```
- Esse caso de uso vai precisar de um novo repositório, para criar ele vamos na pasta `repositories`e vamos criar o arquivo `checkInsRepository.ts` e dentro dele vamos fazer a nossa interface:
```Ts
export interface CheckInsRepository {
	create(data: Prisma.CheckInUncheckedCreateInput): Promise<CheckIn>
}
```
- E agora vamos criar um repositório para fazer os testes, dentro da pasta `inMemory`, vamos criar o arquivo `inMemoryCheckInsRepository.ts`e dentro dele vamos fazer o seguinte:
```ts
import { Prisma, CheckIn } from '@prisma/client'
import { randomUUID } from 'node:crypto'
import { CheckInsRepository } from '../checkInsRepository'

export class InMemoryCheckInsRepository implements CheckInsRepository {
	public items: CheckIn[] = []

	async create(data: Prisma.CheckInUncheckedCreateInput) {
		const checkIn = {
			id: randomUUID(),
			user_id: data.user_id,
			gym_id: data.gym_id,
			validated_at: data.validated_at ? new Date(validated_at) : null,
			created_at : new Date(),
		}

		this.items.push(checkIn)

		return checkIn
	}
	
}
```
- Agora vamos criar os nossos testes, para isso dentro da pasta `useCases`vamos criar o arquivo `checkIn.spec.ts`e vamos escrever os nossos testes:
```ts
import { InMemoryCheckInsRepository } from '@/repositories/inMemory/inMemoryCheckInsRepository'
import { expect, describe, it, beforeEach} from 'vitest'
import { CheckInUseCase } from './checkIn'

let checkInsRepository: InMemoryCheckInsRepository
let sut: CheckInUseCase

describe('Chcek-in Use Case', () => {
	beforeEache(() => {
		checkInsRepository = new InMemoryCheckInsRepository()
		sut = new CheckInUseCase(checkInsRepository)
	})

	it('should be able to check in', async () => {
		const { checkIn } = await sut.execute({
			gymId: 'gym-01',
			userId: 'user-01',
		})

		expect(checkIn.id).toEqual(expect.any(String))
	})
})
```
