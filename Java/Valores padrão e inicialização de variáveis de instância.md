___
- Quando instanciamos um novo objeto, seus `atributos`, são inicializados com valores padrão.
- Cada tipo de variável, recebe um valor padrão, que são:
	- `String` -> recebe o valor `null`;
	- `int` -> recebe o valor 0;
	- `boolean` -> recebe `false`;
- Normalmente os valores padrão dos tipos primitivos numéricos, recebe 0 como valor padrão.
- Quando passamos um tipo de classe para um `atributo`, seu valor também por padrão é `null`;
- Caso queiramos iniciar essas variáveis com valores diferentes de seus valores padrão, atribuímos um valor inicial para esses `atributos`;
```java
public class Carro {
	String fabricante = "Ford";
}
```
- Porém toda vez que [[Instanciando objetos|instanciarmos]] um novo objeto, ele vai ter esse valor como padrão.
