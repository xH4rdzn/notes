___
- Para criar um *Repository*, que por sua vez se conecta com o JPA, precisamos criar uma **interface**, como demostrado no exemplo abaixo:
```java
// MissoesRepository

public interface MissoesRepository extends JpaRepository<MissoesModel, UUID> {}
```
- Basicamente estendemos o *`JpaRepository`* e como parâmetros passamos o *model*, no qual ele se refere e o tipo do ***ID***, que esse *model* possui;
- O *`JpaRepository`*, abstrai métodos já prontos para podermos fazer as *queries*, para o nosso banco de dados. Como o método `save`, `findById`, entre outros métodos.