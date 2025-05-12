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
- Desta maneira já deve ser possível criar `checkIns`em dias diferentes.
- Agora dentro do nosso `CheckInsRepository`