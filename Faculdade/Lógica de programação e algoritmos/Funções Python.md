___
### Funções
- Funções são rotinas de códigos que podem ser executadas quando têm seu nome invocado dentro do programa.
- Exemplos: `print(), input, int, range`
- As funções:
	- Deixam nossos programas mais simples de compreender
	- Confinam *bugs* para dentro delas
	- Tornam programas mais portáveis
	- Auxiliam no trabalho colaborativo
- Para criamos a nossa própria função seguimos o exemplo abaixo:
```python
def realce() :
	# código
```
- Onde `realce` é o nome que damos para a função;
- Os `()` são obrigatórios;
- Para chamarmos uma função invocamos a pelo nome, como no exemplo:
```python
realce()
```

### Parâmetros em Funções
- Parâmetros: dados recebidos pelas funções
- O ato de enviar um dado para uma função é chamado de *passagem de parâmetro*.
- Para criar uma função que recebe um parâmetro seguimos o exemplo:
```python
def realce(s1) :
	# código
```
- Podemos também passar mais de um parâmetro
```python
def sub(x,y):
	# código
```
- Para poder chamarmos essas funções seguimos o exemplo:
```python
realce('Menu')
```
- Se tivermos mais de um parâmetro e quisermos passar fora de ordem, temos que nomear os parâmetros como no exemplo abaixo:
```python
sub2(y = 7, x = 5)
```
###### Parâmetros opcionais
- Podemos dar maior flexibilidade para nossas funções permitindo que nem sempre se use todos os parâmetros na chamada da função
```python
def soma3(x = 0, y = 0, z = 0):
	# código
```

### Escopo de Variáveis
- Um escopo é a propriedade que determina onde uma variável pode ser utilizada dentro de um programa;
###### Escopo Local
- Criado sempre que uma função é chamada
- Variáveis criadas, seja no campo de um parâmetro ou dentro do corpo da função, fazem parte do escopo local daquela função e são chamadas de *variáveis locais*. Essas variáveis só existem dentro daquela própria função.
###### Escopo Global
- Criado no programa principal
- Variáveis globais pertencem a um escopo global e são variáveis criadas dentro do programa principal. Uma *variável global* existe também em todas as funções invocadas ao longo do programa;
###### A instrução global
- Força nosso programa a não criar uma variável local de mesmo nome e manipular somente a global dentro de uma função
```python
def omelete():
	global ovos # usa a variável global
	ovos = 6
	
	
ovos = 12
omelete()
print(ovos)	
```

### Retorno de valores em funções

###### Função x procedimento
- Procedimento (*procedure*) - uma rotina sem retorno
- Função - uma rotina que retorna um dado a quem a invocou

- Para retornar um valor usamos a keyword `return`, como no exemplo abaixo:
```python
def soma3(x = 0, y = 0, z = 0):
	res = x + y + z
	return res
```

### Recursos avançados com funções

###### Exceções comuns em Python
- **ZeroDivisionError** - erro de divisão por zero
- **ValueError** - erro de um dado não esperado sendo digitado
- **IndexError** - erro de índice inexistente sendo acessado;
- Para podermos tratar essas exceções e devolver de maneira mais 'amigável' para o usuário usamos o bloco `try`, como no exemplo abaixo:
```python
while True:
	try:
		x = int(input('Digite um número: '))
		break
	except ValueError:
		print('Oops! Número inválido.Tente novamente...')	
```
- Se quisermos executar um código toda vez, independe se ocorra uma exceção ou não usamos o `finally`

##### Funções lambda
- Funções mais simples, sem nome, chamadas de funções *lambda*
- Elas podem ser escritas em uma só linha de código e dentro do programa principal
- Como no exemplo a seguir:
```python
res = lambda parâmetro: código
```
