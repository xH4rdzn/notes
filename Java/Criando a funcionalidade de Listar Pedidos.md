___
- Agora que criamos a nossa funcionalidade de cadastrar pedidos, agora precisamos listar esses pedidos que já foram feitos.
- Para isso vamos criar na nossa `controller`e criar um novo endpoint, como está no exemplo abaixo:
```java
@GetMapping
public ResponseEntity<> listOrders(
@RequestParam(name = "page", defaultValue = "0") Integer page,
@RequestParam(name = "pageSize", defaultValue="10") Integer pageSize) {

	var order = orderService.findAll(page, pageSize);
	
	
	return ResponseEntity.ok();
}
```
- Agora em nossa service precisamos implementar o método `findAll`, então nela vamos:
```java
public Page<OrderSummaryDTO> findAll(Integer page, Integer pageSize) {}
```
- Agora vamos criar o *`DTO`* de resposta nesse caso o `OrderSummaryDTO
```java
public record OrderSummaryDTO(Long orderId, LocalDateTime orderDate, UUID userId, BigDecimal total) {}
```
- E também vamos criar um *`DTO`*  de resposta para API
```java
public record ApiResponse<T>(List<T> data, PaginationResponseDTO pagination) {}
```
- E agora criamos o `PaginationResponseDTO`
```java
public record PaginationResponseDTO(Integer page, Integer pageSize, Long totalElements, Integer totalPages) {}
```
- Agora em nossa controller, vamos fazer o seguinte:
```java
@GetMapping
public ResponseEntity<ApiResponse<OrderSummaryDTO> listOrders(
@RequestParam(name = "page", defaultValue = "0") Integer page,
@RequestParam(name = "pageSize", defaultValue="10") Integer pageSize) {

	var response = orderService.findAll(page, pageSize);
	
	
	return ResponseEntity.ok(
		new ApiResponse<>(
			response.getContent(),
			new PaginationResponseDTO(response.getNumber(), response.getSize(), response.getTotalElements(), response.getTotalPages());
		
	));
}
```
- Agora em nossa `service`, vamos fazer a lógica de busca e de paginação
```java
public Page<OrderSummaryDTO> findAll(Integer page, Integer pageSize) {
	return orderRepository.findAll(PageRequest.of(page, pageSize))
	.map(entity -> {
		return new OrderSummaryDTO(
			entity.getOrderId(),
			entity.getOrderDate(),
			entity.getUser().getUserId(),
			entity.getTotal()
		);
	});
}
```