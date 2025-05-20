___
- Agora para criarmos nossos testes em relação a localização, podemos fazer da seguinte maneira:
```ts
it('should not be able to check in on distant gym', async () => {

	gymsRepository.items.push({
		id: 'gym-02',
		title: 'Typescritp Gym',
		description: '',
		phone: '',
		latitude: new Decimal(-31.312321),
		longitude: new Decimal(-68.56781),
	})

	await expect(() => 
		sut.execute({
			gymId: 'gym-02',
			userId: 'user-01',
			userLatitude: -13.13131321,
			userLongitude: -49.52315131,
	}),
	).rejects.toBeInstanceOf(Error)

})
```
- Agora dentro do nosso `checkInsUseCase.ts`, precisamos validar as informações de distância;
- Mas para isso dentro da pasta `src`, vamos criar uma pasta com o nome de `utils`e dentro dela vamos criar um arquivo com o nome de `getDistanceBetweenCoordinates.ts`e dentro dele vamos fazer o seguinte:
```ts
export interface Coordinate { 
	latitude: number 
	longitude: number 
} 

export function getDistanceBetweenCoordinates(
	from: Coordinate,
	to: Coordinate,
) {
	if (from.latitude === to.latitude && from.longitude === to.longitude) {
	 return 0 
	}

	const fromRadian = (Math.PI * from.latitude) / 180 
	const toRadian = (Math.PI * to.latitude) / 180

	const theta = from.longitude - to.longitude 
	const radTheta = (Math.PI * theta) / 180

	let dist = Math.sin(fromRadian) * Math.sin(toRadian) + Math.cos(fromRadian) * Math.cos(toRadian) * Math.cos(radTheta)

	if(dist > 1) {
		dist = 1
	}

	dist = Match.acos(dist)
	dist = (dist * 180) / Math.PI
	dist = dist * 60 * 1.1515
	dist = dist * 1.609344

	return dist
}
```
- Agora dentro do nosso `checkInsUseCase`, após a verificação se existe uma academia ou não podemos fazer o seguinte:
```ts
if(!gym) {
	throw new ResourceNotFound()
}

const distance = getDistanceBetweenCoordinates(
{latitude: userLatitude, longitude: userLongitude},
{ latidude: gym.latitude.toNumber(), longitude: gym.longitude.toNumber()}
)

const MAX_DISTANCE_IN_KILOMETERS = 0.1

if(distance > MAX_DISTANCE_IN_KILOMETERS) {
	throw new Error()
}
```