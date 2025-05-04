___
- Em nossos `controllers`, se notarmos toda vez que formos usar um caso de uso, precisamos fazer a instância do repositório e do nosso caso de uso.
- Porém com o crescimento da nossa aplicação é muito comum um caso de uso receber duas ou mais dependências.
- Então usamos esse *pattern* para ficar responsável por fazer a instância das nossas dependências.
- Para usar esse *pattern* dentro da pasta `useCases`vamos criar uma pasta chamada `factories`.
- Vamos nomear os arquivos dessa pasta começando com o verbo `make`, como por exemplo: `makeRegisterUseCase` e dentro desses arquivos vamos fazer como no exemplo abaixo:
```ts
export function makeRegisterUseCase() {
	const usersRepository = new PrismaUsersRepository()
	const registerUseCase = new RegisterUseCase(usersRepository)

	return registerUseCase
}
```
- Agora em nossos `controllers` toda vez que formos fazer o uso do `registerUseCase`, não precisamos importar e nem fazer a instância deles.
- Apenas chamamos a função `makeRegisterUseCase()`.
- Desta maneira se o nosso caso de uso começar a receber mais dependências, bastamos fazer alterações em nossas *factories*.
