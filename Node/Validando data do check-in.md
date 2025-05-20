____
- Agora dentro do `InMemoryCheckInsRepository`, precisamos no método *findByUserIdOnDate* a data.
- Então para podermos validarmos, vamos usar uma biblioteca chamada `dayjs`, para instalar ela vamos usar o comando abaixo:
```zsh
npm i dayjs
```
- Agora vamos dentro do nosso método vamos criar duas datas.
```ts
async findByUserIdOnDate(userId: string, date: Date) {
	const startOfTheDay = dayjs(date).startOf('date')

	const endOfTheDay = dayjs(date).endOf('date')

	const checkInOnSameDate = this.items.find((checkIn) => {

		const checkInDate = dayjs(checkIn.created_at)

		const isOnSameDate = checkInDate.isAfter(startOfTheDay) && checkInDAte.isBefore(endOfTheDay)

		

		return checkIn.user_id === userId && isOnSameDate
	})
}
```
- Agora o teste de fazer *checkIns* em datas diferentes agora passa;
- Agora dentro da pasta `repositories`, vamos criar o arquivo `gymsRepository.ts` e dentro dele vamos fazer o seguinte:
```ts
import { Gym } from '@prisma/client'

export interface GymsRepository {
	findById(id: string): Promise<Gym | null>
}
```
- Agora dentro da pasta `inMemory`, vamos criar o arquivo `inMemoryGymsRepository.ts` e dentro dele vamos fazer o seguinte:
```ts
import {} from '@prisma/client'
import { GymsRepository } from '../gymsRepository'

export class InMemoryGymsRepository implements GymsRepository {
	public items: Gyms[] = []

	async findById(id: string) {
		const gym = this.items.find((item) => item.id === id)
	}

	if(!gym) {
		return null
	}

	return gym
}
```
- Agora dentro do nosso `checkInsUseCase.ts`, precisamos passar outras informações como a localização do usuário e os dados da academia, então adicionamos:
```Ts
interface CheckInUseCaseRequest {
	userId: string
	gymId: string
	userLatitude: number
	userLongitude: number
}
```
- E além de passarmos essas informações, agora precisamos passar que esse *useCase*, necessita do repositório do `gymsRepository`, então adicionamos ao **constructor**
```ts
export class CheckInUseCase {
	constructor(
		private checkInsRepository: CheckInsRepository,
		private gymsRepository: GymsRepository,
	)

	async execute({
		userId,
		gymId,
	}: CheckInUseCaseRequest): Promise<CheckInUseCaseResponse> {
		const gym = await this.gymsRepository.findById(gymId)

		if(!gym) {
			throw new ResourceNotFoundError()
		}

		// Resto do código
	}
}

```
- Agora em nossos testes irão dar um monte de erro, pois agora nosso `checkInsUseCase`, tem duas dependências, então passamos a nova dependência para ele, no método `beforeEach`
```ts
let gymsRepository: InMemoryGymsRepository

beforeEach(() => {
	checkInsRepository = new InMemoryCheckInsRepository()

	gymsRepository = new InMemoryGymsRepository()

	sut = new CheckInUseCase(checkInsRepository, gymsRepository)

	vi.useFateTimers()
})
```
- Nossos testes vão continuar dando erro, pois agora precisamos passar a latitude e a longitude, porém para os testes, só será necessário em testes específicos, então podemos passar o valor como **0**;
- Porém ainda vai continuar dando erro, pois agora temos uma validação se a academia existe ou não, então como ainda não temos o método `create`para cadastrar academias, vamos adicionar uma academia diretamente no array:
```ts
it('should be able to check in', async () => {
	gymsRepository.items.push({
		id: 'gym-01',
		title: 'Javascript Gym',
		description: '',
		phone: '',
		latitude: new Decimal(0),
		longitude: new Decimal(0),
	})

})
```
- Como todos os testes vão precisar de uma academia podemos por o código de criação de academia na função de `beforeEach`, assim garantimos que todos os testes vão ter a academia;
- Desta maneira nossos testes devem passar sem problemas.
