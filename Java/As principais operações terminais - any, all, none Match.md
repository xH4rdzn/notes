___
### noneMatch
- A operação terminal ***noneMatch*** é utilizada para verificar se nenhum elemento de uma stream atende a uma determinada condição. Basicamente, ela retorna ***True*** e se não houver elementos na stream que satisfaçam o predicado fornecido; caso contrário, retorna ***False***.
- Essa operação recebe como argumento um ***Predicate***, que é uma função que retorna um booleano (***True ou False***) para um dado elemento da stream.
```java
var numbers = Arrays.asList(1, 2, 3, 4, 5);

var noneNegative = numbers.stream()
	.noneMatch(number -> number < 0);
	
System.out.println(noneNegative); // true	
```

### anyMatch
- É utilizada para verificar se algum elemento da stream atende a uma determinada condição.
- Basicamente retorna ***True*** se houver pelo menos um elemento que satisfaça o predicado fornecido; caso contrário, retorna ***False***.
- Essa operação recebe como argumento um ***Predicate***, que é uma função que retorna um booleano ***True ou false*** para um dado elemento da stream.
```java
var numbers = Arrays.asList(1, 2, 3, 4, 5);

var anyEven = numbers.stream()
	.anyMatch(number -> number % 2 == 0);
	
System.out.println(anyEven); // true	
```

### allMatch
- É utilizada para verificar se todos os elementos de uma stream atendem a uma determinada condição.
- Basicamente, retorna ***True*** se todos os elementos satisfazerem o predicado forncecido; caso contrário, retorna ***false***.
- Essa operação recebe como argumento um ***Predicate*** que é uma função que retorna um booleano (***True ou false***) para um dado elemento da stream.
```java
var numbers = Arrays.asList(1, 3, 5, 7, 9, 11, 12, 18);

var allPositive = numbers.stream()
	.allMatch(number -> number > 0);
	
System.out.println(allPositive); // true	
```