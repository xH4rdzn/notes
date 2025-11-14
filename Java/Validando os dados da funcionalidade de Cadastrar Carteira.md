___
- Para podermos começar a fazer nossas validações podemos fazer como no exemplo abaixo, que estamos validando os dados do `CreateWalletDTO`
```java
public record CreateWalletDTO(@CPF String cpf, @Email String email, @NotBlank String name) {}
```
- Podemos usar anotações de validação em conjunto.
- Agora que adicionamos as validações em nosso *DTO*, agora em nossa controller, temos que adicionar o `@Valid`, para ele poder fazer a validação dos dados que estão vindo no corpo da requisição
```java
public ResponseEntity<Void> CreateWallet(@RequestBody @Valid CreateWalletDTO dto) {
	// Implementação
}
```