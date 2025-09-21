___
### Ciclo de processamento de dados
- Para escrever mensagens na tela em *Python*, usamos a keyword `print`
```python
print("Olá, mundo!")
```

##### Operadores e operações matemáticas

| Python | Operação                          |
| ------ | --------------------------------- |
| +      | Adição                            |
| -      | Subtração                         |
| **     | Multiplicação                     |
| /      | Divisão (com casas decimais)      |
| //     | Divisão (somente a parte inteira) |
| %      | Módulo / resto da divisão         |
| **     | Exponenciação ou potenciação      |
### Variáveis, dados e seus tipos

###### Regras para nomes de variáveis
- Nunca inicie o nome de uma vairável com um número
```python
2nota
```
- Inicie o nome de uma variável com uma letra ou sublinha(underline)
```python
nota
_nota
```
- Números, letras e sublinhas podem se empregados à vontade no meio
```python
nota5
_n_o_t_a_
```

#### Tipos primitivos de dados
- Numérico (inteiro e ponto flutuante)
- Caractere
- Literal/booleana
###### Variáveis numéricas
- Quando queremos realizar operações aritméticas
- *Inteiro (int)* - números sem casas decimais
- *Ponto Flutuante (float)* - números com casas decimais

###### Variáveis lógicas / booleanas
- Variável para um *bit*. Dois estados:
- **True(verdadeiro)** e **False(falso)**
- Nível lógico alto ou baixo
- 1 ou 0

#### Lista de operadores lógicos em Python e em pseudocódigo

| Python | Operação         |
| ------ | ---------------- |
| ==     | Igualdade        |
| >      | Maior que        |
| <      | Menor que        |
| >=     | Maior ou igual a |
| <=     | Menor ou igual a |
| !=     | Diferente        |
##### Manipulação com strings

#### Concatenação
- Juntar/Somar *strings*
```python
s1 = 'Lógica de programação'
s1 = s1 + ' e Algoritmos'
print(s1)
```
- Repetindo strings na concatenação:
```python
s1 'A' + '-' * 10  + 'B'
```
##### Composição com marcadores de posição
- Juntar diferentes variáveis e strings
```python
nota = 8.5
s1 = 'Você tirou %f naa disciplina de Algoritmos' %nota
print(s1)
```

| Marcador | Tipo                       |
| -------- | -------------------------- |
| %d ou %i | Números inteiros           |
| %f       | Números de ponto flutuante |
| %s       | strings                    |
- Podemos limitar as casas decimais:
```python
nota = 8.5
s1 = 'Você tirou %.2f naa disciplina de Algoritmos' % nota
print(s1)
```
- Podemos também ter várias variáveis:
```python
nota = 8.5
disciplina = 'Algoritmos'
s1 = 'Você tirou %.2f na disciplina de %s' % (nota, disciplina)
print(s1)
```
##### Composição moderna
- Na composição moderna, só adicionamos as `{}`, como demostrado no exemplo abaixo:
```python
nota = 8.5
disciplina = 'Algoritmos'
s1 = 'Você tirou {} na disciplina de {}'.format(nota, disciplina)
```
##### Composição com f-string
- Aqui só adicionamos o `f` antes da *string* e passamos as variáveis entre `{}`, como no exemplo abaixo:
```python
nota = 8.5
disciplina = 'Algoritmos'
s1 = f'Você tirou {nota} na disciplina de {disciplina}'
```

#### Tamanho (length)
- Podemos descobrir o tamanho da cadeia de caracteres com uma função chamada `len`
```python
s1 = 'Lógica de programação e Algoritmos'
print(len(s1))
```

### Função de entrada e fluxo de execução do programa
- Para poder receber informações do usuário usamos a função `input`, e passamos uma mensagem para ela, como no exemplo abaixo:
```python
idade = input('Qual sua idade?')
```

##### Convertendo dados de entrada (casting)
- O `input` sempre retorna um dado do tipo *string*
- Se quisermos um dado numérico, utilizamos aa função *int* ou *float* antes do `input`
```python
nota = float(input('Qual nota você recebeu na disciplina? '))
```
- O **casting** ocorre quando existe a conversão de uma variável de um tipo de dado para outro.