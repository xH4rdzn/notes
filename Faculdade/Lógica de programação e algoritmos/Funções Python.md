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