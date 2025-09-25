___

### Condicional simples e composta
- Para fazer uma condicional simples em `python`, fazemos da seguinte maneira:
```python
if (x > y) :
	# Instruções
```
- Como no exemplo abaixo:
```python
x = int(input('Digite um valor inteiro: '))
y = int(input('Digite um segundo valor inteiro: '))
if (x > y):
	print('O primeiro valor é maior que o segundo')
```
- Para fazer uma condicional composta em `python`, fazemos da seguinte maneira:
```python
x = int(input('Digite um valor inteiro: '))
y = int(input('Digite um segundo valor inteiro: '))
if (x > y):
	print('O primeiro valor é maior que o segundo')
else:
	print('O segundo valor é maior que o primeiro')	
```

### Expressões Lógicas e álgebra booleana

###### Operadores Lógicos

| Python | Pseudocódigo | Operação  |
| ------ | ------------ | --------- |
| not    | não          | negação   |
| and    | e            | conjunção |
| or     | ou           | disjunção |
#### Operador not
- Serve para negar um resultado lógico ou o resultado de uma expressão booleana
- Na prática, isso significa que o resultado final de uma expressão será invertido.

#### Operador and
- Este operador irá prover um resultado verdadeiro se, e somente se, ambas as entradas forem verdadeiras

| v1    | v2    | v1 and v2 |
| ----- | ----- | --------- |
| False | False | False     |
| False | True  | False     |
| True  | False | False     |
| True  | True  | True      |
#### Operador or
- Este operador irá prover um resultado verdadeiro se ao menos uma das entradas for verdadeira

| v1    | v2    | v1 or v2 |
| ----- | ----- | -------- |
| False | False | False    |
| False | True  | True     |
| True  | False | True     |
| True  | True  | True     |

### Condições aninhadas
- Podemos inserir condicionais dentro de outra condicional
- Não existe limite para quantas condicionais podemos colocar dentro da outra
```python
if condicao:
	# código
else:
	if condicao2:
		# código
	else:
		if condicao3:
			# código
		else:
			# código	
```

### Condicional de múltipla escolha (elif)
- Simplifica o uso de múltiplas condicionais em um programa
```python
print('Escolha o que deseja comprar: ')
print('1 - Maça')
print('2 - Laranja')
print('1 - Banana')

produto = int(input('Qual a sua escolha?'))
qtd = int(input('Quantas unidades?'))

if (produto == 1):
	pagar = qtd * 2.3
	print(f'Você comprou {qtd} maças. Total à pagar: {pagar}')
elif (produto == 2):
		pagar = qtd * 3.6
	print(f'Você comprou {qtd} laranjas. Total à pagar: {pagar}')
elif (produto == 3):
		pagar = qtd * 1.85
	print(f'Você comprou {qtd} bananas. Total à pagar: {pagar}')
else:
	print('Produto inexistente!')		
```