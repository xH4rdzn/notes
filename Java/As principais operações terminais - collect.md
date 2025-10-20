___
- A operação terminal ***`collect`*** é utilizada para transformar os elementos de uma stream em outra estrutura de dados, como listas, mapas ou concatenar os elementos em uma única string.
- A função aceita um ***`Collector`*** como argumento, que é uma interface funcional que descreve como transformar uma stream em outro tipo de dado.
- Essa operação é altamente flexível e pode ser personalizada através da utilização da classe utilitária ***`Collectors`***, que fornece diversas implementações comuns de ***`Collector`***.
```java
var names = Arrays.asList("Pedro", "Ana", "Marcos", "Vanessa");

var filteredNames = names.stream()
	.filter(name -> name.length() => 6)
	.collect(Collectors.toList());
```
- Podemos filtrar informações e concatenar todas essas informações em uma única ***String***, separados por algo que passamos como argumento, como no exemplo a seguir:
```java
var result = products.stream()
	.filter(product -> product.getPrice() < 500)
	.map(Product::getName)
	.collect(Collectors.joining(","));
```
- No exemplo acima passamos como parâmetro do ***`joining`*** o que queremos que faça a separação dos resultados obtidos do nosso ***`filter`***;
	- Usamos o ***`Collectors.joining`*** para poder fazer a concatenação;
- Podemos também agrupar informações, como é demonstrado no exemplo a seguir:
```java
// Agrupando clientes pelo mês de aniversário
var result = clients.stream()
		.collect(Collectors.groupingBy(client -> client.getBirthDate().getMonth(), Collectors.counting()));
```
- Para agrupar informações usamos o ***`Collectors.groupingBy`***, no qual recebe como parâmetro o filtro pelo qual queremos agrupar essas informações;
- E para retornar a contagem dessas informações usamos o ***`Collectors.couting`***, que retorna a contagem de elementos nesse caso já separado pelo agrupamento.
- Podemos fazer o mapeamento de informações agrupadas, como no exemplo abaixo:
```java
var result = clients.stream()
	.collect(Collectors.groupingBy(Client::getAge, Collectors.mapping(Client::getName, Collectors.toList())));
```
- No exemplo estamos agrupando as informações por *idade* e estamos fazendo um mapeamento, no qual uma *idade*, vai ter uma lista de nomes para cada grupo de *idade*;
- ***Podemos agrupar, mapear e concatenar tudo de uma vez, caso precisarmos***, como no exemplo abaixo:
```java
var result = clients.stream()  
        .collect(Collectors.groupingBy(Client::getAge, Collectors.mapping(Client::getName, Collectors.joining(";"))));
```