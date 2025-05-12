___
- ***TDD*** -> Test Driven Development
- Com o ***TDD*** começamos a fazer as nossas funcionalidades pelo teste, assim os testes nos ajudam a validar a nossa funcionalidade e regras de negócio antes de fazer a sua implementação. **Grosso modo**
- Então no nosso arquivo de testes de `checkIn`, escrevemos outro teste
```Ts
it('should not be able to check in twice in the same day', async () => {
	await sut.execute({
		gymId: 'gym-01',
		userId: 'user-01',
	})

	
	await expect(() => sut.execute({
		gymId: 'gym-01',
		userId: 'user-01'
	})).rejects.toBeInstance(Error)
})
```
- Normalmente usamos *TDD*, quando temos uma regra de negócio mais **complexas**. 
- Com o *TDD* temos 3 etapas, que são: `red`, `green`e `refactor`
- No estado *red*, significa que o teste deve dar erro, após isso vamos para o próximo estado.
- O próximo estado *green*, codamos o mínimo possível para o teste passar, para depois ir para o próximo estado que é o *refactor*.
- O estado *refactor*, é quando refatoramos o nosso código.
- Sempre que possível o nosso teste unitário, deve ser o mais especifico possível.
- O `vitest`, tem uma funcionalidade chamada `mocking`, que usamos para podermos usar datas em nossos testes.
- *Mocking*, é quando criamos valores fictícios para dados ou funções.
- Para usar essa funcionalidade fazemos como no exemplo abaixo:
```ts
beforeEach(() => {
	checkInsRepository = new InMemoryCheckInsRepository()

	sut = new CheckInUseCase(checkInsRepository)

	vi.useFakeTimers()

})


afterEach(() => {
	vi.useRealTimers()
})


it('should not be able to check in twice in the same day', async () => {
	vi.setSystemTime(new Date(2022, 0, 20, 8, 0, 0))
	

	await sut.execute({
		gymId: 'gym-01',
		userId: 'user-01',
	})

	
	await expect(() => sut.execute({
		gymId: 'gym-01',
		userId: 'user-01'
	})).rejects.toBeInstance(Error)
})
```
- Agora voltamos ao nosso *repositório* e criamos um novo método para o `CheckInsRepository`
```ts
findByUserIdOnDate(userId: string, date: Date): Promise<CheckIn| null>
```
- Agora no nosso `InMemoryCheckInsRepository`, precisamos implementar esse novo método, da maneira mais simples póssivel
```ts
async findByUserIdOnDate(user: string, date: Date) {
	const checkOnSameDate = this.items.find(checkIn => checkIn.user_id === userId)

	if(!checkOnSameDate) {
		return null
	}
}
```
- Agora vamos no nosso *useCase* e fazemos a seguinte verificação:
```ts
async execute({
	userId,
	gymId,
}: CheckInUseCaseRequest): Promise<CheckInUseCaseResponse> {

	const checkInOnSameDate = await this.checkInsRepository.findByUserIdOnDate(userId, new Date())

	if(checkInOnSameDate) {
		throw new Error()
	}

	const checkIn = await this.checkInsRepository.create({
		gym_id: gymId,
		user_id: userId,
	})

	return {
		checkIn,
	}
}
```
- Agora ao executarmos o nosso teste, ele deve passar
- Agora também podemos criar mais testes, como o teste abaixo:
```ts
it('should be able to check in twice but in different days', async () => {
	vi.setSystemTime(new Date(2022, 0, 20, 8,0,0))


	await sut.execute({
		gymId: 'gym-01',
		userId: 'user-01',
	})

	vi.setSystemTime(new Date(2022, 0, 21, 8, 0, 0))
	const {checkIn} = await sut.execute({
		gymId: 'gym-01',
		userId: 'user-01',
	})

	expect(checkIn.id).toEqual(expect.any(String))
})
```
- Porém se rodarmos esse teste agora dará erro, pois só estamos validando pelo *ID* do usuário e não pela data.
