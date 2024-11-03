___
- Quando fazemos uma composição entre objetos para usar o objeto que está dentro de outro também precisa ser instanciado.
- Podemos fazer da seguinte maneira:
```java
Carro meuCarro = new Carro();
meuCarro.proprietario = new Pessoa();
```
- Agora podemos atribuir os valores para o proprietário da seguinte maneira:
```java
meuCarro.proprietario.nome = "Igor";
```
- Outra maneira de fazer essa atribuição é passando um objeto já instanciado para a propriedade:
```java
Pessoa eu = new Pessoa();
eu.nome = "Igor Coelho";
eu.cpf = "111.222.333-44";
eu.anoNascimento = 1998;

Carro meuCarro = new Carro();
meuCarro.proprietario = eu;
```
