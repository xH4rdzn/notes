___
### Variáveis
- **Simples**: armazenam somente um dado
- **Compostas**: armazenam um conjunto de dados
### Estrutura de dados
- É um conjunto de dados organizados de uma maneira específica na memória do programa.
- A maneira como os estão organizados na memória, como podem ser buscados, manipulados e acessados, é o que define e diferencia as estrutura de dados.
### Tuplas
- Estrutura de dados *estática*
- A tupla é *imutável*
- Representada em *Python* por `()`
```python
mochila = ('Machado', 'Camisa', 'Bacon', 'Abacate')

# Acessando
print(mochila[0])
```

### Desempacotamento de parâmetros em funções
- Suponha que você quer realizar o somatório de diversos valores, porém não sabe quantos valores serão somados. Pode ser que sejam somente 2, ou então 10, ou mesmo 100 números
- Como criar uma função capaz de receber um número tão variável de parâmetros?
```python
def soma(*num):
	acumulador = 0
	print(f'Tupla: {num}')
	for i in num:
		acumulador += i
		return acumulador
		
# Programa principal
print(f'Resultado: {soma(1,2)}\n')	
print(f'Resultado: {soma(1,2,3,4,5,6,7,8,9)}\n')		
```

### Listas
- Estrutura de dados *dinâmica*
- Podemos alterar dados e tamanho
- Indexadas por valores numéricos inteiros
- Representadas em *Python* por `[]`
```python
mochila = ['Machado', 'Camisa', 'Bacon', 'Abacate']

# Mudando um dado
mochila[2] = 'Laranja'
```
- Podemos manipular as listas, com os métodos
```python
# Adicionando no final da lista
mochila.append('Ovos')

# Insere na posição informada
mochila.insert(1, 'Canivete')

# Removendo itens

## Deletando o indice informado 
del mochila[1]

## Deleta o dado informado
mochila.remove('Ovos')
```
- Para poder fazermos uma cópia de uma lista podemos fazer da seguinte maneira:
```python
lista_original = [5, 7, 9, 11]
lista_copia = lista_original[:]
```

### Strings e listas dentro de listas

###### Dupla Indexação
- O primeiro índice é referente a cada item da lista
- O segundo índice é referente a cada caractere da string
- Assim, podemos acessar não só cada dado dentro da lista, mas também cada caractere das strings de um índice da lista

##### Listas dentro de listas
- É possível colocar listas dentro de listas.
```python
mochila = [['Cebola', 0.39], ['Tomate', 0.49], ['Maçã', 0.89]]
```
- Por exemplo para pegar o conjunto de dados da 'cebola' iramos fazer assim:
```python
mochila[0] # Retorna ['Cebola', 0.39]
```
- Se quisermos acessar apenas a string fariamos assim:
```python
mochila[0][0] # Retorna 'Cebola'
```
- E para pegar apenas o valor da seguinte maneira:
```python
mochila[0][1]
```

### Dicionários
- Estrutura de dados *dinâmica*
- Podemos alterar dados e tamanho
- Indexados por chaves (palavras-chave)
- Representado em Python por `{}`
```python
game = {
	'nome': 'Super Mario',
	'desenvolvedora': 'Nintendo',
	'ano': 1990
}

print(game)
```
- Para acessar os valores de acordo com as palavras-chave, fazemos da seguinte maneira:
```python
print(game['nome'])
```
##### Métodos para dicionários
- *values*: obtém somente os dados
- *keys*: obtém somente as chaves
- *items*: obtém o par chave:dado
```python
# Retorna apenas os valores sem as chaves
print(game.values())

# Retorna apenas as chaves
print(game.keys())

# Retorna o par chave-valor
print(game.items())
```
- Podemos fazer *loops* nesses métodos
```python
# Apenas os valores
for values in game.values():
	print(values)
	
# Apenas as chaves
for keys in game.keys():
	print(keys)	
	
# O conjunto chave-valor
for keys, values in game.items():
	print(f'{keys} = {values}')	
```

##### Listas com dicionários
- Uma lista contendo, em cada índice, um dicionário
```python
games = []
game1 = {
	'nome': 'Super Mario',
	'videogame': 'Super Nintendo',
	'ano': 1990
}

game2 = {
	'nome': 'Zelda',
	'videogame': 'Nintendo 64',
	'ano': 1998
}

game3 = {
	'nome': 'Pokemon',
	'videogame': 'Game Boy',
	'ano': 1999
}

games = [game1, game2, game3]
print(games)
```

### Trabalhando com métodos em strings
- *Uma string é imutável*
- Mas, com listas, podemos alterá-la
```python
# Isso da erro
s1 = 'Algoritmos'
print(s1)
s1[0] = 'a'

# Para fazer isso
s1 = list('Algoritmos')
print(s1)
print(''.jon(s1))
s1[0] = 'a'
print(''.join(s1))
```
###### Relação de métodos para uso com strings

| Função/Método      | Objetivo                                                                     |
| ------------------ | ---------------------------------------------------------------------------- |
| `starswith`        | Verifica se caracteres existem no início da string                           |
| `endswith`         | Verifica se caracteres existem no final da string                            |
| `lower`            | Converte string para minúscula                                               |
| `upper`            | Converte string para maiúscula                                               |
| `find`             | Busca a primeira ocorrência de um padrão de caracteres em uma string         |
| `rfind`            | Idêntico ao `find`, mas inicia a busca da direita para a esuqerda            |
| `center`           | Centraliza uma string                                                        |
| `ljust`, `rjust`   | Ajustam uma string com alinhamentos à esquerda ou à direita, respectivamente |
| `split`            | Divide uma string                                                            |
| `replace`          | Substitui caracteres em uma string                                           |
| `lstrip`, `rstrip` | Removem espaços em branco à esquerda ou à direita, respectivamente           |
| `strip`            | Remove espaços em branco das extremidades                                    |

