___
### Teoria dos conjuntos
- Um conjunto está associado a um agrupamento de elementos. Estes elementos podem ser números, letras, objetos, pessoas, dentre muitas outras possibilidades. Considerando os conjuntos numéricos, por exemplo, o primeiro deles surgiu a partir da necessidade do ser humano de realizar contagens.
- Números naturais (N):
	- N = {1, 2, 3, 5...}
	- N = {0, 1, 2, 3, 4, 5,...}
- Números inteiros (Z):
	- Z = {...-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5,...}
- Números racionais (Q);
	![[Pasted image 20251128195659.png]]
	- O símbolo ∈ significa “pertence” e é utilizado para relacionar elementos e conjuntos. 
	- Quando um elemento faz parte de um determinado conjunto, dizemos que este elemento pertence ao conjunto e utilizamos o símbolo ∈ .Quando o elemento não pertence ao conjunto, o símbolo utilizado é ∉.
- Números irracionais (I);
- Números reais (R):
	- Conjunto que mistura os números racionais e irracionais.


### Vetores e Matrizes
- Na computação, o uso de vetores e de matrizes é muito importante e útil. Vamos começar a falar um pouco sobre vetores.
- Geometricamente, um vetor consiste em um segmento de reta que possui um comprimento, uma direção e um sentido.
- Vetores são utilizados na representação de grandezas que não podem ser descritas apenas por um número. Estas grandezas são chamadas de _grandezas vetoriais_. A força, por exemplo, é uma grandeza vetorial.
- Para podermos criar um array em python, com números, precisamos usar a **numpy**,para podermos fazer operações com esse *VETOR/ARRAY* então podemos fazer como no exemplo abaixo:
```python
import numpy as np

v = np.array([[2, 4, 5, 9]])
print(v)
```
- Considere o vetor v que armazena os preços de venda, em dólares, de algumas mercadorias anunciadas em um comércio eletrônico:
	- v = (22, 12, 54, 89, 11)
- Supondo que cada dólar corresponde a 5 reais, obtenha um vetor u que contém os preços dessas mercadorias, mas em reais.
```python
import numpy as np

v = np.array([[22, 12, 54, 89, 11]])
u = 5 * v
print(u)
```
- Podemos também fazer a subtração entre vetores, como no exemplo abaixo:
```python
import numpy as np

v = np.array([[22, 12, 54, 89, 11]])
u = np.array([[18, 4, 39, 61, 8]])
m = v - u
print(m) # Retorna [[4 8 15 28 3]]
```
- Podemos realizar somas:
```python
import numpy as np
v = np.array([[22, 12, 54, 89, 11]])
t = np.array([[3, 2, 1, 4, 1]])
w = v + t
print(w) # Retorna [[25 14 55 93 12]]
```
- Podemos usar para outras aplicações, uma que chamamos de produto escalar, que são a multiplicação de vetores e o resultado é um número
```python
import numpy as np

notas = np.array([[90, 85, 70, 100]])
pesos = np.array([[0.2, 0.2, 0.3, 0.3]])
media = np.inner(notas, pesos)
print(media)
```

#### Matrizes
- Uma matriz é um conjunto retangular formado por linhas e colunas, representado entre colchetes ou entre parênteses
![[Pasted image 20251129130305.png]]
- Para podermos fazer uma matriz em *python*, podemos fazer como no exemplo a seguir:
```python
import numpy as np

A = np.array([[3, 2, -1], [5, 0, 20]])
print(A)
```
- Com matrizes, podemos realizar operações de soma:
```python
import numpy as np

F1 = np.array([[400, 10], [480, 12], [600, 15]])
F2 = np.array([[31, 11], [37,11], [48, 11]])
custoTotal = F1 + F2
print(custoTotal)
```
- Podemos fazer a multiplicação de seus valores
```python
import numpy as np

F1 = np.array([[400, 10], [480, 12], [600, 15]])
F1 = 1.1 * F1
print(F1)
```
- Mas também podemos fazer a multiplicação entre matrizes:
```python
import numpy as np

A = np.array([[3, 1, 3], [6, 5, 5]])
B = np.array([[100, 50], [50, 100], [50, 50]])
C = np.matmul(A, B)
print(C)
```

### Funções
- Uma função de uma variável é uma relação que existe entre elementos x e y pertencentes a dois conjuntos distintos, um chamado de _domínio_ e o _outro_, de contradomínio.
- Para que tenhamos uma função, cada elemento do domínio, o conjunto dos possíveis valores da variável independente x precisa estar relacionado a um único elemento do contradomínio, conjunto das variáveis dependentes.
- Todos os elementos do contradomínio que estão relacionados aos elementos do domínio formam um conjunto chamado de _conjunto imagem_. O conjunto imagem é um subconjunto do contradomínio, ou seja, os elementos do conjunto imagem também são elementos do contradomínio.
- Em *python*, podemos fazer a representação gráfica utilizando a biblioteca `matplotlib.pyplot`, como é demonstrado no exemplo abaixo:
```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 10, 100)
y = 28 * x
plt.plot(x, y)
plt.show()
```
- A função y=28x é chamada de _função linear_. De um modo geral, uma função é chamada de linear quando tem a forma:
$$
y=ax+b
$$
- O termo _a_ é o coeficiente angular e indica a taxa de crescimento ou de decrescimento da função, e o termo _b_ é o coeficiente linear e indica o ponto no qual o gráfico da função intercepta o eixo y.
- Temos também a *função quadrática*:
$$
	y = ax² + bx + c
$$
- Onde *a*, *b* e *c* são constantes e *a* é diferente de zero
![[Pasted image 20251129132801.png]]
- O *Xv* é o valor associado eixo x, ao vértice da parábola
- O *Yv* é o valor referente ao eixo y, ao vértice da parábola.
- Para podermos fazer uma função quadrática em *python*, podemos seguir como no exemplo abaixo:
```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 16, 100)
y = -340*x**2 + 5700 * x -9500
plt.plot(x, y)
plt.show()
```
- Como já temos os valores de *a, b* e *c*, podemos calcular os nossos vértices
```python
a = -340
b = 5700
c = -9500

xv = -b/ (2*a)
print(xv)

delta = b **2 - 4 * a * c
yv = -delta/ (4 * a)
print(yv)
```

### Polinômios
- Os polinômios estão relacionados a muitos problemas práticos. Podemos gerar imagens por meio de polinômios a partir de pontos específicos.
- As fontes que vemos na tela do celular, tablet ou do computador, por exemplo, são geradas por polinômios interpoladores. A partir de um conjunto de pontos colocados adequadamente, por meio de polinômios os pontos são interligados e as fontes são obtidas.
- Fenômenos físicos, tais como o movimento de um objeto sendo lançado ao ar ou a trajetória relacionada a um salto, podem ser modelados por meio de polinômios.
- A partir de um conjunto de pontos, podemos obter facilmente o polinômio que passa por estes pontos. Este processo é chamado de _interpolação polinomial_.
- Para fazer isso em *python*, podemos fazer como no exemplo a seguir:
```python
from scipy.interpolate import *
x = []
y = []
p = lagrange(x, y)
print(p)
```
- Exemplo:
	- Obtenha, por meio de *PYTHON*, o polinômio que interpola os pontos A(4, 2), B(7, -1), C(10, 12) e D(11, 15)
```python
from scipy.interpolate import *
x = [4, 7, 10, 11]
y = [2, -1, 12, 15]
p = lagrange(x, y)
print(p)
```

### Noções de aritmética modular
- Em muitos problemas reais, trabalhamos com um número finito de números ou de letras e precisamos realizar operações aritméticas relacionadas a estes elementos.
- O exemplo mais comum e conhecido é o relógio analógico. Sabemos que para indicar as horas, estes relógios possuem números que variam de 1 a 12. Se o relógio está marcando 10 horas e temos um compromisso daqui a 5 horas, o compromisso será às 15 horas. No entanto, no relógio, não há o número 15, pois o maior deles é 12. Neste caso, podemos pensar, inicialmente, de uma forma intuitiva: 10+2=12, que é o maior número existente no relógio, mas como ainda temos 3 horas para chegarmos em 15, na hora do compromisso o relógio analógico estará marcando 3 horas. Logo, em um relógio analógico, 10+5=3. Pode parecer um pouco estranho escrevermos que 10 mais 5 é igual a 3, mas não estamos trabalhando, neste caso, com o conjunto dos números naturais, mas sim com um subconjunto finito. Para possibilitar a resolução de diversos problemas parecidos com este, existe uma aritmética específica denominada de _aritmética modular_.
- A aritmética modular relacionada às vogais é mod 5, pois há 5 vogais e aritmética modular relacionada às letras do alfabeto é mod 26, pois há 26 letras no alfabeto.
