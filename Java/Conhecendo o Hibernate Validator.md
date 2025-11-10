___
### O que é o Hibernate Validator ?
- É a implementação de referência da especificação ***Bean Validation (JSR 380)***.
- Ele é usado para validar dados de entrada através de annotations.

### Validações disponíveis
- `@CPF`
- `@CNPJ`
- `@NotNull`
- `@NotBlank`
- `@Min(value)`
- `@Size`
- `@Email`
- `@NotEmpty`
- `@Max(value)`
- `@Positive`
- `@Negative`
- entre outras

### Como usamos essas validações
- Podemos utilizar diretamente nos atributos de nossas classes.
- Para efetuarmos a validação, indicaremos através da anotação `@Valid`;
- Podemos ver nos exemplos abaixo de como aplicar as validações e ativar essa validação:
- Definindo as validações
```java
class User {

	@CPF
	private String cpf;
	
	@Min(18)
	private Long age;
	
}
```
- Ativando a validação
```java
void(@Valid User user) {
	// código
}
```