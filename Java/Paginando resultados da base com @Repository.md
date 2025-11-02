___
- Já vimos anteriormente como retornar os [[Consultando todos os dados da base com @Repository|todos os registros do banco de dados]], mas uma uma boa prática é faze a paginação desses registros, uma vez que pode se ter muitos registros, assim deixando a nossa API lenta.

### Recebendo parâmetros de paginação
- Quando estamos fazendo paginação precisamos receber seus dois principais parâmetros que são a ***página*** e o ***tamanho da página***.
- Que podemos receber da seguinte maneira:
```java
public ReponseEntity<Page<UserEntity>> listAll(
	@RequestParam(name = "page", defaultValue = "0") Integer page,
	@RequestParam(name = "pageSize", defaultValue= "10") Integer pageSize
) {

	var users = userService.findAll(page, pageSize);
	
	
	return ReponseEntity.ok(users);
}
```

### Implementando a paginação com PageRequest
- Agora em nossa `service`, podemos fazer o uso do `PageRequest`, passando para ele os parâmetros que são enviados da nossa `controller`, e passamos ele para o nosso `repository`.
```java
public Page<UserEntity> findAll(Integer page, Integer pageSize) {
	
	var pageRequest = PageRequest.of(page, pageSize);
	
	return userRepository.findAll(pageRequest);
}
```

### Reestruturando o retorno da API
- Para melhorar o retorno vamos fazer os seguintes passos:
- Criar um *DTO* de resposta com os parâmetros:
```java
public record ApiResponseDTO<T>(List<T> data, PaginationResponseDTO pagination) {}
```
- Criar um novo *DTO*, para paginação:
```java
public record PaginationResponseDTO(Integer page, Integer pageSize, Long totalElements, Integer totalPages) {}
```
- Voltamos a nossa `controller`e alteramos seu retorno para:
```java
@GetMapping
public ReponseEntity<ApiResponseDTO<UserEntity>> listAll(
	@RequestParam(name = "page", defaultValue = "0") Integer page,
	@RequestParam(name = "pageSize", defaultValue= "10") Integer pageSize
) {

	var pageResponse = userService.findAll(page, pageSize);
	
	
	return ReponseEntity.ok(new ApiResponseDTO<>(
		pageResponse.getContent(),
		new PaginationResponse(pageResponse.getNumber(), pageResponse.getSize(), pageResponse.getTotalElements(), pageResponse.getTotalPages())
	));
}
```