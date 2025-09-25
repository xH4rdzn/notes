___
### Estrutura de repetição
- Estrutura no programa em que todas as intruções contidas nela se repetem de maneira indefinida, até que uma condição seja satisfeita.
- Sinônimos: *estrutura iterativa*, *laço de repetição* ou *loop de repetição*

### Estrutura de repetição while
- Repete um bloco de instruções enquanto determinada condição se mantiver verdadeira
- Caso contrário, ocorre o desvio para a primeira linha de código após este bloco de repetição.
- Sintaxe:
```python
while (x > y):
	# Código
```
- Exemplo:
```python
x = 1
while (x <= 5):
	print(x)
	x += 1
```
##### Variável de controle
- Define a condição de parada com que o laço é executado
- Chamamos de *iterador* a variável de controle que realiza a contagem do número de vezes que o laço está sendo executado
##### Variáveis contadoras e acumuladoras
- Contadoras
	- Acrescentam valores constantes em uma variável
- Acumuladoras
	- Acumulam totais, como um somatório

### Tópicos importantes com laços em Python

##### Operadores especiais de atribuição

| Operador | Exemplo | Equivalente |
| -------- | ------- | ----------- |
| +=       | x += 1  | x = x + 1   |
| -=       | x -= 1  | x = x - 1   |
| *=       | x *=2   | x = x * 2   |
| /=       | x /= 2  | x = x / 2   |
| **=      | x **= 2 | x = x ** 2  |
| //=      | x //= 4 | x = x // 4  |

##### Instrução *break*
- A instrução *break* serve para encerrar um laço de repetição abruptamente, independentemente do estado da variável de controle do laço

##### Instrução *continue*
- O comando *continue* serve para retornar o laço ao início a qualquer momento, independentemente do estado variável de controle da condicional do laço

##### Valores Truthy e Falsey
- Dados não booleanos também podem ser tratados como *True* ou *False* em uma condição, seja esta de uma estrutura condiocionada ou de um laço
- *Falsey/False*
	- Número zero (int ou float) e string vazia
- *Truthy/True*
	- Qualquer outro dado

### Estrutura de repetição *for*
- Assim como o `while`, essa estrutura repete um bloco de instruções enquanto uma condição se mantiver verdadeira
- No entanto, diferentemente do `while`, o *for* é empregado em situações em que *o número de vezes que o laço irá executar é finito e bem definido.*
```python
for i in range (6) :
	print(i)
```
- Quando passamos apenas um valor entre `()`, esse é valor final, **lembrando que começa do 0**
- Podemos alterar isso para a seguinte maneira:
```python
for i in range(0, 6, 1):
	# código
```
- Onde o primeiro valor é o *valor inicial do iterador*;
- O segundo valor é o *valor final do iterador*
- O terceiro valor é o *passo do iterador*
###### Varredura de string
- Podemos passar por todos os caracteres de uma *string* usando um laço *for*
```python
frase = "Lógica de Programação e Algoritmos"
for i in range(0, len(frase), 1):
	print(frase[i], end="")
```
- Podemos passar o `end=""`, para tirar a quebra de linha do `print()`;
### Estruturas de repetição aninhadas
- Podemos colocar um laço de repetição dentro de outro laço de repetição. Como demostrado no exemplo abaixo:
```python

```