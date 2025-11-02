___
- Como vimos anteriormente, podemos acrescentar métodos [[Filtrando resultados da base com QueryMethod do @Repository|utilizando os Querys Methods]], mas outra maneira de fazer isso é através do uso da anotação `@Query`, assim, fazemos uma query nativa e diretamente para o banco de dados.
- Para utilizar essa anotação, a fazemos diretamente na `interface`, como é demonstrado no exemplo abaixo:
```java
@Repository
public interface UserRepository extends JpaRepository<UserEntity, Long> {

	@Query(value = "SELECT * FROM tb_users WHERE name = ?1",
	countQuery = "SELECT COUNT(*) tb_users WHERE name =?1",	
	 nativeQuery = true
 )
	Page<UserEntity> findByName(String name, PageRequest pageRequest);
	
	Page<UserEntity> findByAgeGreaterThanEqual(Long age, PageRequest pageRequest);

	Page<UserEntity> findByNameAndAgeGreaterThanEqual(String name, Long age, PageRequest pageRequest);
}
```
- Separamos os parâmetros por `?1`, onde o número é a ordem dos parâmetros;
- Quando utilizamos uma query nativa, e estamos utilizando o `PageRequest`, o nome do atributo que irá fazer a ordenação não é mais o atributo da classe, mas sim o nome da coluna no banco de dados.
- Se tivermos um *erro*, temos que fazer a implementação do método `findAll` através de query Nativa também;