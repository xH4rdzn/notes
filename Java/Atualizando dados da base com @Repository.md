___
- Para criar um endpoint para fazer atualização dos dados usamos o método `PUT`;
- Para fazermos isso podemos seguir como no exemplo abaixo:
```java
@PutMapping(path = "/{userId}")
public ResponseEntity<Void> updateUser(@PathVariable("userId") Loong userId,
			@RequestBody UpdateUserDTO dto) {

		userService.updateById(userId, dto);
			
}
```
- Agora em nossa `service`, implementamos esse método
```java
public Optional<UserEntity> updateById(Long userId, UpdateUserDTO dto) {

	var user userRepository.findById(userId)
	
	if (user.isPresent()) {
		// Código
	}
	
	return user
	
}
```
- Agora como esse retorno pode também não existir em nosso `controller`, fazemos a seguinte tratativa:
```java
@PutMapping(path = "/{userId}")
public ResponseEntity<Void> updateUser(@PathVariable("userId") Loong userId,
			@RequestBody UpdateUserDTO dto) {

		var user = userService.updateById(userId, dto);
		
		return user.isPresent() ?
			ResponseEntity.noContent().build() :
			ReponseEntity.notFound().build();
	
}
```
- Agora podemos terminar a implementação em nossa `service`
```java
public Optional<UserEntity> updateById(Long userId, UpdateUserDTO dto) {

	var user userRepository.findById(userId)
	
	if (user.isPresent()) {
		if(StringUtils.hasText(dto.name())) {
			user.get().setName(dto.name());
		}
		
		if(!isNull(dto.age())) {
			user.get().setAge(dto.age());
		}
		
		userRepository.save(user.get());
	}
	
	return user
	
}
```
- E agora podemos passar toda essa lógica para um método privado para podermos deixar o nosso código de maneira mais limpa
```java
public Optional<UserEntity> updateById(Long userId, UpdateUserDTO dto) {
	
	var user = userRepository.findById(userId);
	
	if(user.isPresent()) {
		updateFields(dto, userId);
		
		userRepository.save(user.get());
	}
	
}


private void updateFields(UpdateUserDTO dto, Optional<UserEntity> user) {
	if(hasText(dto.name())) {
		user.get().setName(dto.name());
	}
	
	if(!isNull(dto.age())) {
		user.get().setAge(dto.age());
	}
}
```
- Agora podemos atualizar parcialmente ou completamente os dados, basta passar os campos que queremos pelo corpo da requisição.