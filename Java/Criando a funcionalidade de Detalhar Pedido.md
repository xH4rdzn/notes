___
- Agora podemos também criar um endpoint, para pegar apenas um pedido em específico e detalhar ele.
- Para isso em nossa controller, vamos criar mais um endpoint do tipo `GET`, como no exemplo abaixo:
```java
@GetMapping("/{orderId}")
public ResponseEntity<OrderResponseDTO> findById(@PathVariable("orderId") Long orderId) {

	var order = orderService.findById(orderId);
	
	
	return order.isPresent() ?
		ResponseEntity.ok(OrderResponseDTO.fromEntity(order.get())) :
		ReponseEntity.notFound().build(); 
} 
```
- Agora em nossa `service` criamos o método findById:
```java
public Optional<OrderEntity> findById(Long orderId) {
	return orderRepository.findById(orderId);
}
```
- Agora vamos criar o nosso `OrderResponseDTO`
```java
public record OrderResponseDTO(Long orderId, BigDecimal total, LocalDateTime orderDate, UUID userId, List<OrderItemResponseDTO> items) {

	public static OrderResponseDTO fromEntity(OrderEntity entity) {}

}
```
- E agora vamos criar o `OrderItemResponseDTO`
```java
public record OrderItemResponseDTO(BigDecimal salePrice, Integer quantity, ProductResponseDTO product) {}
```
- E agora precisamos criar o `ProductResponseDTO`
```java
public record ProductResponseDTO(Long productId, String productName, List<TagResponseDTO> tags) {}
```
- E também vamos precisar do `TagResponseDTO`
```java
public record TagResponseDTO(Long tagId, String name) {}
```
- Agora voltado ao método `fromEntity`, vamos fazer todo o mapeamento
```java
public record OrderResponseDTO(Long orderId, BigDecimal total, LocalDateTime orderDate, UUID userId, List<OrderItemResponseDTO> items) {

	public static OrderResponseDTO fromEntity(OrderEntity entity) {
		
		return new OrderResponseDTO(
			entity.getOrderId(),
			entity.getTotal(),
			entity.getOrderDate(),
			entity.getUser().getUserId(),
			getItems(entity.getItems())
		);
	}

	private static List<OrderItemResponseDTO> getItems(List<OrderItemEntity> items) {
		return items.stream()
		.map(OrderItemResponseDTO::fromEntity)
		.toList();
	}

}
```
- Agora em nosso `OrderItemReponseDTO`vamos adicionar o método
```java
public record OrderItemResponseDTO(BigDecimal salePrice, Integer quantity, ProductResponseDTO product) {

	public static OrderItemResponseDTO fromEntity(OrderItemEntity entity) {
		return new OrderItemResponseDTO(
			entity.getSalePrice(),
			entity.getQuantity(),
			ProductResponseDTO.fromEntity(entity.getId().getProduct())
		)
	}

}
```
- Agora em nosso `ProductResponseDTO`vamos adicionar o método:
```java
public record ProductResponseDTO(Long productId, String productName, List<TagResponseDTO> tags) {

	public static ProductResponseDTO fromEntity(ProductEntity product) {
		return new ProductResponseDTO(
			product.getProductId(),
			product.getProductName(),
			getTags(product.getTags())
		)
	}
	
	private static List<TagResponseDTO> getTags(List<TagEntity> tags) {
		
		return tags.stream()
			.map(TagResponseDTO::fromEntity)
			.toList();
		
	}

}
```
- E agora em nosso `TagResponseDTO`, vamos adicionar o método `fromEntity`
```java
public record TagResponseDTO(Long tagId, String name) {

	public static TagResponseDTO fromEntity(TagEntity entity) {
		
		return new TagResponseDTO(
			entity.getTagId(),
			entity.getName()
		)
		
	}

}
```