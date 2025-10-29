___
- Para criar a nossa primeira entidade usando o JPA Hibernate, podemos seguir o exemplo abaixo:
```java
@Entity
@Tables(names = "pratos")
public class Prato {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Integer id;
	
	private String nome;
	
	private String decricao;
	
	private Boolean disponivel;
	
	private BigDecimal valor;
	
	@Column(name = "data_registro")
	private LocalDateTime dataDeRegistro = LocalDateTime.now();
	
	// Getters, Setters e Construtores
}
```
- ***`@Entity`*** -> Anota que a classe vai ser uma entidade no banco de dados.
- ***`@Table`*** -> Podemos fazer configurações para a entidade, que será criada como tabela no banco de dados, como definir o *`name`*;
- ***`@Id`*** -> Definimos que aquele atributo será a nossa chave primária;
- ***`@GeneratedValue`***-> Podemos definir uma *strategy* para gerar valores de maneira automática para a chave primária.
- ***`@Column`***-> Usamos, para poder definir configurações específicas da coluna/atributo como o *`name`* da tabela;