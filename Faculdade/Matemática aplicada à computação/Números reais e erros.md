___
### Norma IEEE 754
- A norma **IEEE 754** apresenta um padrão a ser seguido pelos fabricantes de computadores e pelas empresas responsáveis pela construção de compiladores de linguagens científicas no que se refere ao uso da linguagem binária.
- Surgiram pela necessidade de resolver problemas de condicionamento que geram erros indesejados por questões de armazenamento de dados numéricos, métodos de  arredondamento, procedimentos de realização de operações aritméticas básicas (soma, subtração, multiplicação e divisão).
- Com a norma **IEEE 754**, a precisão numérica para a representação de números reais é definida como sendo, simples, dupla ou estendida;

### Representação de números reais
- O conjunto dos números reais é formado pela união do conjunto dos números racionais com o conjunto dos números irracionais;
- Relação biunívoca entre os números reais e os pontos de uma reta
- Os computadores geralmente utilizam a base binária para a representação de números
- Há uma quantidade fixa de bits e, consequentemente, um conjunto finito de números que podem ser representados por meio de computadores
- Notação científica:
$$
	x = +-(M)b * b^n
$$
- em que M é a mantissa e n é o expoente
- b -> 10
- Por exemplo, o número 210,687 pode ser escrito na base decimal (b = 10) em notação científica de diferentes formas:
	- 210,687 = 210,687 x 10⁰
	- 210,687 = 21,0687 x 10¹
	- 210,687 = 2,10687 x 10²
	- 210,687 = 21068,7 x 10⁻²
	- 210,687 = 2106,87 x 10⁻¹
- Notação científica normalizada:
	- 210,687 -> 2,10687 x 10²
- Exemplo
	- Escreva a representação do número 3242 utilizando a notação científica normalizada
$$
	3242 = 3,242 * 10³
$$
- Em python, podemos fazer da seguinte maneira:
```python
a = 3242
print('%.10e' % a)
```
- Utilizando a notação científica normalizada faça a representação do número 0,23241
$$
	0,23241 = 2,3241 * 10⁻¹
$$
```python
a = 0.23241
print('%.4e' % a)
```
- Obtenha a representação do número 0,0000054 por meio da notação científica normalizada
$$
	0,0000054 = 5,4 * 10⁻⁶
$$
- De acordo com a norma **IEEE 754**, números reais podem ser representados na forma simples, dupla ou estendida.
- Representação simples: 32 bits em que o primeiro está associado ao sinal do número (0 quando positivo ou 1 quando negativo), os oito bits seguintes se referem ao expoente que pode variar de -126 a 127 e os 32 bits restantes correspondem à mantissa.
![[Pasted image 20251126215437.png]]
-  ![[Pasted image 20251126215519.png]]

### Aritmética de ponto flutuante
- Soma:
	- Exemplo com expoentes iguais:
		- Dados os números decimais a = 2,3421 x 10² e b = 3,5154 x 10², calcule a + b
$$ a + b = 2,3421 * 10² + 3,5154 * 10² $$
$$ a + b = (2,3421 + 3,5154) * 10²$$
$$ a + b = 5,8575 * 10² $$
	- Exemplo com expoentes diferentes:
		- Dados os números decimais a = 2,3421 x 10² e b = 3,5154 x 10⁴, calcule a + b
$$ a + b = 2,3421 * 10² + 3,5154 * 10⁴ $$
$$ a + b = 0,023421 * 10⁴ + 3,5154 * 10⁴ $$
$$ a + b = (0,023421 + 3,5154) * 10⁴ $$
$$ a + b = 3,538821 * 10⁴$$
- Subtração
	- Exemplo:
		- Dados os números decimais a + 2,3421 x 10² e b = 3,5154 x 10², calcule a - b
$$ a - b = 2,3421 * 10² - 3,5154 * 10² $$
$$  a - b = (2,3421 - 3,5154) * 10² $$
$$ a - b = -1,1733 * 10²$$
- Multiplicação
	- Exemplo:
		- Dados os números decimais a = 2,3421 x 10² e b = 3,5154 x 10², calcule o produto entre a e b.
$$ a . b = 2,3421 * 10² * 3,5154 * 10² $$
$$a . b = (2,3421 * 3,5154) * (10² * 10²)$$
$$a.b = 8,23341834 * 10⁴$$
- Divisão:
	- Obtenha a divisão de a = 2,3421 x 10² por b = 3,5154 x 10²
$$ a / b = 2,3421 * 10² / 3,5154 * 10² $$
$$ a / b = (2,3421 / 3,5154) * (10² / 10²)$$
$$ a / b = 0,66623997269 * 10⁰$$
$$ a / b = 6,6623997269 * 10⁻¹$$
### Representação de erros
- É muito comum a existência de erros quando tratamos de representações numéricas e operações por meio de computadores. Estes erros podem ocorrer devido às aproximações feitas em muitas representações numéricas que são erros de arredondamento. Outro tipo de erro muito comum é o erro por truncamento.