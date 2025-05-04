___
- Em nossos testes, fazer a instancia do *repositório* e do *caso de uso*, são comuns em todos os testes, e assim tendo muita duplicidade de código.
- Para resolver isso vamos fazer com faça a instância deles antes de todos os testes.
- Para isso vamos acessar o nosso arquivo de testes e vamos fazer o seguinte:
```ts
// Antes do *describe*
let usersRepository: InMemoryUsersRepository
let sut: RegisterUseCase

// No começo do nosso teste, dentro do *describe*
	beforeEach(() => {
		usersRepository = new InMemoryUsersRepository()
		sut = new RegisterUseCase(usersRepository)
	})

```
- E fazemos isso para todos os nossos arquivos de testes. Apenas trocando os casos de uso.