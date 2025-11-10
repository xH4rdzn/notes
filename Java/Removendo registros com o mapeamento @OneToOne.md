___
- Quando temos que deletar um registro do banco de dados que possui diversos relacionamentos, podemos fazer como no exemplo abaixo:
```java
// UserService.java

public boolean deleteById(UUID userId) {
	
	var user = userRepository.findById(userId);
	
	if(user.isPresent()) {
		userRepository.deleteById(userId);
		billingAddressRepository.deleteById(user.get().getBillingAddress().getBillingAddressId());
	}
	
	return user.isPresent();
	
}
```
- Como a nossa entidade `User`, depende de `BillingAddress`, para poder fazermos a deleção, precisamos fazer de maneira invertida.
- Primeiro apagamos o registro de `User`e depois apagamos o registro de `BillingAddress`, como está no exemplo acima