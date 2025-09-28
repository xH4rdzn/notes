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
