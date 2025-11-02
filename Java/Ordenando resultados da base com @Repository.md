___
- Como fizemos a [[Paginando resultados da base com @Repository|paginação dos resultados]] agora podemos ordenar esse retorno.
- Para isso vamos passar um novo parâmetro em nosso `controller` e passamos ele para nossa `service`
```java
@GetMapping
public ReponseEntity<ApiResponseDTO<UserEntity>> listAll(
	@RequestParam(name = "page", defaultValue = "0") Integer page,
	@RequestParam(name = "pageSize", defaultValue= "10") Integer pageSize,
	@RequestParam(name = "orderBy", defaultValue="desc") String orderBy
) {

	var pageResponse = userService.findAll(page, pageSize, orderBy);
	
	
	return ReponseEntity.ok(new ApiResponseDTO<>(
		pageResponse.getContent(),
		new PaginationResponse(pageResponse.getNumber(), pageResponse.getSize(), pageResponse.getTotalElements(), pageResponse.getTotalPages())
	));
}
```
- Agora na nossa `service`, alteramos ele para ficar da seguinte maneira:
```java
public Page<UserEntity> findAll(Integer page, Integer pageSizem String orderBy) {

	var direction = Sort.Direction.DESC;
	if(orderBy.equalsIgnoreCase("asc")) {
		direction = Sort.Direction.ASC;
	} 
	
	var pageRequest = PageRequest.of(page, pageSize, direction, "campo");
	
	return userRepository.findAll(pageRequest);
}
```
- Em ***"campo"***, passamos o nome do atributo pelo qual queremos ordenar nossos registros.