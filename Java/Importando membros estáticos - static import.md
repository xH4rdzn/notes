___
- Podemos *importar* membros estáticos, sem precisar importar toda a classe.
- Podemos fazer essa importação apenas em membros estáticos de uma classe.
- Como no exemplo abaixo que importamos apenas o método ***calcularAreaQuadrado***;
```java
import static com.algaworks.matematica.CalculadoraArea.calcularAreaQuadrado;
```
- E agora para usarmos, podemos chamar apenas pelo nome do método:
```java
double areaQuadrado = calcularAreaQuadrado(5.2);
```
- Se quisermos importar todos os membros estáticos de uma classe, podemos fazer da seguinte maneira:
```java
import static com.algaworks.matematica.CalculadoraArea.*;
```
