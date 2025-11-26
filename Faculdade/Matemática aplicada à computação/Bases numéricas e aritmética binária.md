___
### Conceitos de Bases Numéricas
- O sistema de numeração que utilizamos é posicional de base 10:
	- 0, 1, 2, 3, 4, 5, 6, 7, 8 e 9
- Base binária (b = 2) -> 0, 1
- Base quinária (b = 5) -> 0, 1, 2, 3 e 4
- Base Octal (b = 8) -> 0, 1, 2, 3, 4, 5, 6 e 7
- Base decimal (b = 10) -> de 0 à 9
- Base hexadecimal (b = 16)

### Base Numérica Binária
- A base binária, tem esse nome, pois ela é baseada em dois símbolos, que são o 0 e 1;
- É bastante utilizada, principalmente na computação por conta da variação de corrente.
- A base binária é um sistema posicional de numeração que conta com dois símbolos, 0 e 1.

| Decimal | Binário | Byte     |
| ------- | ------- | -------- |
| 0       | 0       | 00000000 |
| 1       | 1       | 00000001 |
| 2       | 10      | 00000010 |
| 3       | 11      | 00000011 |
| 4       | 100     | 00000100 |
| 5       | 101     | 00000101 |
- Conversão de números binários para númericos decimais:
1. Escrevemos o número binário a ser convertido
2. A cada dígito, da direita para esquerda, escrevemos as respectivas potências da base b =2 com os expoentes variando de 0, 1, 2 e assim por diante, ou seja, 2⁰, 2¹, 2²...
3. Multiplicamos os dígitos pelas respectivas potências e somamos os resultados
4. O número obtido é o decimal equivalente ao número binário
- Exemplo:
	- Converta o número binário 110101 em decimal
$$
	N = 1 * 2⁵ + 1 * 2⁴ + 0 * 2³ + 1 * 2² + 0 * 2¹ + 1 * 2⁰
$$
$$
	N = 1 * 32 + 1 * 16 + 0 * 8 + 1 * 4 + 0 * 2 + 1 * 1
$$
$$
	N = 32 + 16 + 0 + 4 + 0 + 1
$$
$$
	N = 53
$$
- Conversão de números decimais para números binários
- Exemplo:
	- Converta o número decimal 25 para o respectivo número binário
- Para poder converter fazemos a divisão do número decimal por 2, pegamos o seu resultado e seu resto.
- Dividimos até o resultado chegar a zero
- Pegamos todos os restos da ultima operação para a primeira
![[Pasted image 20251125205336.png]]
- Podemos organizar em tabelas também, como é demonstrado a seguir:

| Decimal | Quociente (divisão por 2) | Resto |
| ------- | ------------------------- | ----- |
| 25      | 12                        | 1     |
| 12      | 6                         | 0     |
| 6       | 3                         | 0     |
| 3       | 1                         | 1     |
| 1       | 0                         | 1     |
|         | Forma binário: 11001      |       |
- Exemplo
	- Dado o número 28 na forma decimal, qual é a respectiva representação na forma binária ?

| Decimal | Quociente (divisão por 2) | Resto |
| ------- | ------------------------- | ----- |
| 28      | 14                        | 0     |
| 14      | 7                         | 0     |
| 7       | 3                         | 1     |
| 3       | 1                         | 1     |
| 1       | 0                         | 1     |
|         | Forma binária: 11100      |       |

### Base Numérica Hexadecimal
- A base hexadecimal utiliza de 0 a 9 e as letras de A à F, no total temos 16 símbolos associados a essa base.
- A base numérica hexadecimal é um sistema posicional em que a base é 16. Para a representação de números hexadecimais são utilizados os símbolos: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E e F
- O número decimal 1504, por exemplo, precisa de 11 dígitos para ser representado na forma binária (10111100000) e de apenas 3 dígitos para se representado na forma hexadecimal (5e0);
- Conversão de números hexadecimais em números decimais:
	1. Escrevemos o número hexadecimal a ser convertido
	2. Transformamos cada dígito A, B, C, D, E e F para o respectivo decimal 10, 11, 12, 13, 14 e 15
	3. A cada dígito, da direita para a esquerda, escrevemos as respectivas potências da base b = 16 com os expoentes variando de 0, 1, 2 e assim por diante, ou seja 16⁰, 16¹...
	4. Multiplicamos os dígitos pelas respectivas potências e somamos os resultados
	5. O número obtido é o número decimal equivalente ao número hexadecimal
- Converta o hexadecial 2E5C em um número decimal
![[Pasted image 20251125212037.png]]
- Conversão de números decimais em números hexadecimais:


### Algoritmos de conversão de base
- Para conversão de um número decimal inteiro em um binário, temos a função `bin()`, em *Python*
- Se por exemplo, quisermos a forma binária do número 25, basta fazermos `bin(25)`
```python
bin(25)
# Ele retorna -> '0b11001'
```
- Para retornar apenas o número em binário podemos fazer da seguinte maneira:
```python
bin(25)[2:]
# Ele retorna '11001'
```
- Exemplo:
```python
numero = int(input('Informe um número inteir: '))
print(f'O binário correspondente é: {bin(numero)[2:]}')
```
- Para obtermos o hexadecimal correspondente ao decimal 11868, por exemplo, basta fazermos `hex(11868)`
```python
hex(11868)
# Ele retorna -> '0x2e5c'
```
- Podemos usar o mesmo exemplo usando anteriormente, mudando apenas a função para `hex()`
- Agora vamos implementar o próprio algoritmo para converter de um número decimal para binário em *Python*
```python
numero = int(input('Digite um número inteiro: '))
binario = ''
while numero > 0:
	binario += str(numero % 2)
	numero //=2
print(f'O binário correspondente é: {binario[::-1]}')	
```

### Aritmética Binária
- A soma de dois números binários segue o mesmo princípio da soma de números decimais, mas é importante lembrar que, na soma de números binários, 1 + 1 = 10
$$
	1001 + 0101 = 1110
$$
- Outro exemplo:
$$
	1001 + 1101 = 10110
$$
