___
- Podemos incrementar ainda mais no [[Consultando todos os dados da base com @Repository|endpoint de listagem]], com os ***Query Methods***, para podermos fazer uso dele, podemos incrementar ainda mais no mesmo endpoint:
```java
@GetMapping
public ReponseEntity<ApiResponseDTO<UserEntity>> listAll(
	@RequestParam(name = "page", defaultValue = "0") Integer page,
	@RequestParam(name = "pageSize", defaultValue= "10") Integer pageSize,
	@RequestParam(name = "orderBy", defaultValue="desc") String orderBy,
	@RequestParam(name = "name", required=false) String name,
	@RequestParam(name = "age", required=false) Long age
) {

	var pageResponse = userService.findAll(page, pageSize, orderBy, name, age);
	
	
	return ReponseEntity.ok(new ApiResponseDTO<>(
		pageResponse.getContent(),
		new PaginationResponse(pageResponse.getNumber(), pageResponse.getSize(), pageResponse.getTotalElements(), pageResponse.getTotalPages())
	));
}
```
- Agora como queremos criar uma consulta personalizada, podemos acessar o nosso `repositório`, que até o momento só tem a extensão para o `JpaRepository`, e podemos criar métodos abstratos, como no exemplo abaixo:
```java
@Repository
public interface UserRepository extends JpaRepository<UserEntity, Long> {

	Page<UserEntity> findByName(String name, PageRequest pageRequest);
	
	Page<UserEntity> findByAgeGreaterThanEqual(Long age, PageRequest pageRequest);

	Page<UserEntity> findByNameAndAgeGreaterThanEqual(String name, Long age, PageRequest pageRequest);
}
```
- Lembrando que são utilizados certas palavras chaves para que seja criado a *query sql* de maneira automática, podemos ler mais na [documentação](https://docs.spring.io/spring-data/jpa/reference/jpa/query-methods.html);
- Agora na nossa `service`, podemos fazer as seguinte alteração:
```java
public Page<UserEntity> findAll(Integer page, Integer pageSizem String orderBy) {

	var direction = Sort.Direction.DESC;
	if(orderBy.equalsIgnoreCase("asc")) {
		direction = Sort.Direction.ASC;
	} 
	
	var pageRequest = PageRequest.of(page, pageSize, direction, "campo");
	
	if(hasText(name) && !isNull(age)) {
		return userRepository.findByNameAndAgeGreaterThanEqual(name, age, pageRequest);
	}
	
	if(hasText(name)) {
		return userRepository.findByName(name, pageRequest);
	}
	
	if(!isNull(age)) {
		return userRepository.findByAgeGreaterThanEqual(age, pageRequest);
	}
	
	return userRepository.findAll(pageRequest);
}
```