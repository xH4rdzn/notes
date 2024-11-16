___
- O `Response Entity`, permite devolver uma reposta mais apropriada para o `client`, ela disponibiliza métodos que informam o `Status Code` e podemos devolver até mesmo um corpo;
- Para fazer o uso dela, seguimos o exemplo abaixo:
```java
@GetMapping("/exemplo")
public ResponseEntity<Object> metodoResponse() {
	return ReseponseEntity.status(404).body("corpo da resposta");
}
```