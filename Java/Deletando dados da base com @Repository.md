___
- Para podermos deletar dados do banco de dados, criamos um *endpoint* com o método `DELETE`;
- Para criar o *endpoint* com esse método usamos a anotação `@DeleteMapping`, como é demonstrado no exemplo abaixo:
```java
@DeleteMapping(path = "/{userId}")
public ResponseEntity<Void> deleteById(@PathVariable("userId") Long userId) {}
```
- Agora na service podemos fazer da seguinte maneira:
```java
public boolean deleteById(Long userId) {
	
	
	var exists = userRepository.existsById(userId)
	
	if(exists) {
		userRepository.deleteById(userId);
		return true;
	}
	
	return false;
}
```
- Agora voltamos ao nosso `controller`, para terminar a implementação
```java
@DeleteMapping(path = "/{userId}")
public ResponseEntity<Void> deleteById(@PathVariable("userId") Long userId) {

	var userDeleted = userService.deleteById(userId);
	
	return userDeleted ?
		ResponseEntity.noContent().build() :
		ResponseEntity.notFound().build();

}
```