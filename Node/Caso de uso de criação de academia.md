___
- Dentro da pasta `useCases`, vamos criar o arquivo `createGymUseCase.ts` e dentro dele vamos fazer o seguinte:
```ts
interface CreateGymUseCaseRequest {
	title: string
	description: string | null
	phone: string | null
	latitude: number
	longitude: number
}

interface CreateGymUseCaseResponse {
	gym: Gym
}

export class CreateGymUseCase {
	constructor(private gymsRepository: GymsRepository) {}

	async execute({
		title,
		description,
		phone,
		latitude,
		longitude,
	}: CreateGymUseCaseRequest): Promise<CreateGymUseCaseResponse> {
	
		
	}
}
```