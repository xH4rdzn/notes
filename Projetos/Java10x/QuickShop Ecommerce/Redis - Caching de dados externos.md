___
- O *Redis* é um banco de dados de estrutura de dados em memória, open-source e altamente performático, que pode ser usado como cache, broker de mensagens ou até mesmo como um banco de dados completo. Ele armazena dados como strings, listas, conjuntos, hashes e mais, tudo na memória RAM, o que faz com que as operações sejam extremamente rápidas em comparação com bancos de dados tradicionais, que dependem do armazenamento em disco.
- O *Redis* é amplamente utilizado para melhorar a performance de aplicações, principalmente em cenários onde é necessário acessar ou armazenar dados rapidamente, como no caso de caches.

### Principais comandos do Redis (redis-cli)
- Conectar no Redis
```zsh
redis-cli -h localhost -p 6379 -a sa
```
- Definir um valor
```zsh
SET chave "valor"
```
- Obter um valor
```zsh
GET chave
```
- Verificar o TIL (Time to Live)
```zsh
TIL chave
```
- TIL valido redis retorna o tempo, sem tempo de expiração -1, chave não existe -2;
- Ver todas as chaves
```Zsh
KEYS *
```
- Deletar uma chave
```zsh
DEL chave
```
- Sair
```zsh
QUIT
```
- Se quisermos adicionar um *time to live* para uma chave que não possui
```Zsh
EXPIRE chave tempoEmSegundos
```

### Implementando no Spring como cache
- Em nossa *Service*, precisamos anotar os métodos que queremos que ele armazene as informações em cache:
```java
@Cacheable(value = "products")
public List<PlaziProductResponse> getAllProducts() {
	return plaziStoreClient.getAllProducts();
}

@Cacheable(value = "product", key = "#productId")
public PlaziProductResponse getProductById(Long productId) {
	return plaziStoreClient.getProductById(productId);
}
```
- Agora no nosso arquivo principal, precisamos anotar, para que ele faça o cache
```java
@EnableCaching
```