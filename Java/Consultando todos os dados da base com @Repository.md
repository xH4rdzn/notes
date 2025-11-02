___
### Construção de endpoint @GetMapping
- Para podermos recuperar dados criados em nosso banco de dados usamos o método HTTP do tipo *`GET`*;
- Então em nosso `controller`, criamos um método com anotado com ***`@GetMapping`***
```java
@GetMapping
public ResponseEntity<List<UserEntity>> listAll() {
	userService.findAll();
}
```

### Consultando banco de dados
- Agora em nossa `service`, precisamos implementar o método que criamos no `controller`, que podemos fazer seguindo o exemplo:
```java
public List<UserEntity> findAll() {
	return userRepository.findAll();
}
```
- Agora podemos voltar ao `controller` e terminar a implementação:
```java
@GetMapping
public ResponseEntity<List<UserEntity>> listAll() {
	var users = userService.findAll();
	
	return ResponseEntity.ok(users);
}
```