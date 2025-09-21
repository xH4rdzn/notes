___
- O *Response Entity*, serve para podermos devolver respostas customizadas para as nossas requisições;
- Como por exemplo trocar o *status code* da resposta;
- Podemos usar o `ResponseEntity`, podemos seguir como no exemplo abaixo:
```java
public ResponseEntity<String> criarNinja(@RequestBody NinjaDTO ninja) {
	NinjaDTO ninjaDTO = ninjaService.criarNinja(ninja);
	return ResponseEntity.status(HttpStatus.CREATED).body("Ninja criado com sucesso");
}
```