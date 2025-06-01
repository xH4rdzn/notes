___
- Expressões lógicas assim como [[Expressões Comparativas]], ao ser avaliadas elas resultam em um *valor verdade*.

### Operadores Lógicos

| Operador | Significado |
| :------: | :---------: |
|    &&    |      E      |
|   \|\|   |     OU      |
|    !     |     NÃO     |

### Operador E
- Para o *valor verdade* que usa o operador `&&`,  resulte em verdadeiro ***todas as condições*** precisam ser **verdadeiras**.
```
Suponha x igual a 5

x <= 20 && x == 10 -> Resultado Falso

x > 0 && x != 3 -> Resultado Verdadeiro

x <= 20 && x == 10 && x != 3 -> Resultado Falso
```
##### Tabela verdade do operador `&&`

| A   | B   | A && B |
| --- | --- | ------ |
| F   | F   | F      |
| F   | V   | F      |
| V   | F   | F      |
| V   | V   | V      |
### Operador OU
- Para o *valor verdade* que usa o operador `||`, resulte em verdadeiro ***pelo menos uma condição deve ser verdadeira***.
```
Suponha x igual a 5

x == 10 || x < 20 -> Resultado Verdadeiro

x > 0 || x != 3 -> Resultado Verdadeiro

x <= 0 || x != 3 || x != 5 -> Resultado Verdadeiro
```
##### Tabela verdade do operador `||`

| A   | B   | A \|\| B |
| --- | --- | -------- |
| F   | F   | F        |
| F   | V   | V        |
| V   | F   | V        |
| V   | V   | V        |
### Operador NÃO
- Esse operador ***inverte a condição***
```
Suponha x igual a 5
!(x == 10) -> Resultado Verdadeiro
	F

!(x >= 2) -> Resultado Falso
	V

!(x <= 20 && x == 10) -> Resultado Verdadeiro
	V           F
```
##### Tabela verdade do operador `!`

| A   | !A  |
| --- | --- |
| F   | V   |
| V   | F   |
