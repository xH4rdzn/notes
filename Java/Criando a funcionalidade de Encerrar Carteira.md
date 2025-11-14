___
- Para criar essa funcionalidade em nossa API, vamos em nossa controller de `Wallet`, e vamos adicionar um endpoint do tipo `DELETE`, como demonstrado no exemplo abaixo:
```java
@DeleteMapping(path = "{/walletId}")
public ResponseEntity<Void> deleteWallet(@PathVariable("walletId") UUID walletId) {

	walletService.deleteWallet(walletId);

}
```
- Agora em nossa `service`, vamos implementar a lógica para podermos fazer a deleção desse registro no banco de dados.
```java
public boolean deleteWallet(UUID walletId) {

	var wallet = walletRepository.findById(walletId);

	if(wallet.isPresent()) {
	
		if (wallet.get().getBalance().compareTo(BigDecimal.ZERO) != 0) {
			throw new DeleteWalletException("The Balance is not zero. The current amount is $" + wallet.get().getBalance());
		}
		
		walletRepository.deleteById(walletId);
	}
	
	
	return wallet.isPresent();
}
```
- Retornamos uma `boolean`, para podermos informar se conseguimos ou não fazer a deleção desse registro do banco de dados. (`true`, para informar que o registro foi apagado e `false` para informar que não foi removido)
- Agora podemos criar a nossa exceção de `DeleteWalletException`
```java
public class DeleteWalletException extends JBankException {

	private final String detail;
	
	
	public DeleteWalletException(String detail) {
		super(detail);
		this.detail = detail;
	}
	
	@Override
	public ProblemDetail toProblemDetail() {
		var pd = ProblemDetail.forStatus(HttpStatus.UNPROCESSABLE_ENTITY);
		
		pd.setTitle("You cannot delete this wallet");
		pd.setDetail(detail);
		
		return pd;
	}

}
```
- Agora podemos terminar a nossa lógica em nossa `controller`
```java
@DeleteMapping(path = "{/walletId}")
public ResponseEntity<Void> deleteWallet(@PathVariable("walletId") UUID walletId) {

	var deleted = walletService.deleteWallet(walletId);
	
	return deleted ?
		ResponseEntity.noContent().build() :
		ReponseEntity.notFound().build();
	

}
```