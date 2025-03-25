___
### Bases numéricas
- A base decimal utiliza os algoritmos -> 0, 1, 2, 3, 4, 5, 6, 7, 8, 9;
- A base binária utiliza apenas os algarismos 0 e 1;
- A base octal utiliza os algarismos 0, 1, 2, 3, 4, 5, 6 e 7;
- A base hexadecimal utiliza os algarismos 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 e as letras A, B ,C , D, E e F.

### Conversão de binário para decimal
- Considere o número (*1100110*)
- Os passos são os seguintes:
	- Contar as posições de cada bit da direita para a esquerda, começando por zero.

| 6   | 5   | 4   | 3   | 2   | 1   | 0   |
| --- | --- | --- | --- | --- | --- | --- |
| 1   | 1   | 0   | 0   | 1   | 1   | 0   |
- Multiplicar cada algarismo pela potência de 2 referente à sua posição, somando esses valores:

| 6      | 5      | 4      | 3      | 2      | 1      | 0      |
| ------ | ------ | ------ | ------ | ------ | ------ | ------ |
| 1      | 1      | 0      | 0      | 1      | 1      | 0      |
| 1 x 2⁶ | 1 x 2⁵ | 0 x 2⁴ | 0 x 2³ | 1 x 2² | 1 x 2¹ | 0 x 2⁰ |
| 64     | 32     | 0      | 0      | 4      | 2      | 0      |
- Somando todos os valores o resultado é *102*;
- Sendo assim o número em base binária (1100110) é igual a 102 na base decimal;

### Conversão de octal para decimal
- Considere o número (*2703*)
- Os passos são os seguintes:
	- Contar as posições de cada bit da direta para a esquerda, começando por zero.

| 3   | 2   | 1   | 0   |
| --- | --- | --- | --- |
| 2   | 7   | 0   | 3   |
- Multiplicar cada algarismo pela potência de 8 referente à sua posição, somando esses valores:

| 3       | 2      | 1      | 0      |
| ------- | ------ | ------ | ------ |
| 2       | 7      | 0      | 3      |
| 2 x 8³  | 7 x 8² | 0 x 8¹ | 3 x 8⁰ |
| 2 x 512 | 7 x 64 | 0 x 8  | 3 x 1  |
| 1024    | 448    | 0      | 3      |
- Somando todos os valores da: *1475*;
- Assim o número (2703) na base octal, transformado para decimal representa: *1475*;

### Conversão de hexa para decimal
- Considere o número (*B3F*)
- Lembrando que a seq. numérica é: 0...9 e A = 10, B = 11, C = 12, D = 13, E = 14 e F = 15.
- Os passos são os seguintes:
- Contar as posições de cada bit da direita para a esquerda, começando por 0

| 2   | 1   | 0   |
| --- | --- | --- |
| B   | 3   | F   |
- Multiplicar cada algarismo pela potência de 16 referente à sua posição, somando esses valores

| 2        | 1       | 0        |
| -------- | ------- | -------- |
| B        | 3       | F        |
| B x 16²  | 3 x 16¹ | F x 16⁰  |
| 11 x 16² | 3 x 16¹ | 15 x 16⁰ |
| 11 x 256 | 3 x 16  | 15 x 1   |
| 2816     | 48      | 15       |
- Somando todos esses valores o valor (*B3F*) da base hexadecimal, transformado em decimal equivale a *2879*;