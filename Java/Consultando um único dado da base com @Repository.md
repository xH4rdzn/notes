___
- Para podermos fazer isso, também vamos ter um endpoint do tipo `GET`, mas ela precisa de um parâmetro de rota, para podermos receber esse parâmetro de rota, podemos fazer como no exemplo a seguir:
```java
@GetMapping(path = "/{userId})
public ResponseEntity<UserEntity> findById(@PathVariable("userId") Long userId) {
	
	userService.findById(userId);
	// Falta terminar a implementação
}
```
- Agora em nossa `service`, podemos fazer da seguinte maneira:
```java
public Optional<UserEntity> findById(Long userId) {
	return userRepository.findById(userId);
}
```
- Agora voltamos para a nossa `controller`, para terminar a implementação
```java
@GetMapping(path = "/{userId})
public ResponseEntity<UserEntity> findById(@PathVariable("userId") Long userId) {
	
	var user = userService.findById(userId);
	
	return user.isPresent() ?
		ResponseEntity.ok(user.get()) :
		ResponseEntity.notFound().build();
	
}
```