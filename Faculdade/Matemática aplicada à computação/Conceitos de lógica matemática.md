___
### Proposições
-  Conjunto de palavras ou símbolos que retratam um pensamento de sentido completo e que pode ser classificado como verdadeiro ou falso.
- Exemplos:
	- 4 é par -> Verdadeira
	- Paris é a capital da França -> Verdadeira
	- 4 + 1 = 10 -> Falsa
##### Princípios
1. Princípio da não contradição: uma proposição não pode ser classificada como verdadeira e falsa simultaneamente
2. Princípio do terceiro excluído: uma proposição é verdadeira ou falsa, e não existe a possibilidade de um terceiro caso.
- Proposição verdadeira, usamos ou `V`ou o número `1`
- Para proposição falsa, usamos o `F`ou o número `0`
- Exemplos:
	- p: 10 > 2, V(p) = V
	- q: 3 é um número par, V(q) = F

#### Proposições compostas
- P: Júlia é médica ***ou*** Júlia é advogada
- Q: Gustavo trabalha durante o dia ***e*** Gustavo estuda à noite
- Uma proposição composta, são utilizadas proposições simples e conectores com outra proposição.
- R: ***Se*** Anderson estudar, ***então*** terá um bom desempenho nas avaliações
- S: ***Não*** é verdade que 2 é maior do que 4
- T: Vou comprar um carro ***se e somente se*** receber um aumento salarial

### Operadores Lógicos Simples (NOT, AND e OR)

#### Negação (~p ou p')
- A negação de uma proposição, é basicamente negar o valor lógica dela.
- Se por exemplo uma proposição ter o valor verdadeiro, a negação dela é falsa
- Tabela verdade:

| p   | p'  |
| --- | --- |
| V   | F   |
| F   | V   |
- Porta Lógica:
![[Pasted image 20251124195705.png]]
- Exemplos:
- A proposição p: 2 + 3 = 5 é verdadeira e a negação ~p 2+3!=5 é uma proposição falsa. Logo, V(p) = V e V(~p) = F
- A proposição q: 4-2=2 é verdadeira e ~q:4-2!=2 é falsa. Logo, V(q)=V e V(~q)= F
#### Conjunção (^ ou .)
- A conjunção é diretamente associada ao `E`;
- Tabela verdade:

| p   | .   | q   |
| --- | --- | --- |
| V   | V   | V   |
| V   | F   | F   |
| F   | F   | V   |
| F   | F   | F   |
- Só obtemos o valor `V`, verdadeiro, caso as duas proposições sejam verdadeiras, como é demonstrado na tabela verdade acima.
- Porta Lógica:
![[Pasted image 20251124201241.png]]
#### Disjunção (v ou +)
- A disjunção é diretamente associada ao `Ou`;
- Tabela Verdade:

| p   | +   | q   |
| --- | --- | --- |
| V   | V   | V   |
| V   | V   | F   |
| F   | V   | V   |
| F   | F   | F   |
- Só obtemos o valor `F`, caso todas as proposições sejam falsas.
![[Pasted image 20251124205241.png]]

### Operadores Lógicos Avançados (NAND, NOR E XOR)

### NAND
- É a negação da conjunção `E`;
- Tabela verdade

| ~   | (p  | .   | q)  |
| --- | --- | --- | --- |
| F   | V   | V   | V   |
| V   | V   | F   | F   |
| V   | F   | F   | V   |
| V   | F   | F   | F   |
#### NOR
- Tabela verdade

| ~   | (p  | +   | q)  |
| --- | --- | --- | --- |
| F   | V   | V   | V   |
| F   | V   | V   | F   |
| F   | F   | V   | V   |
| V   | F   | F   | F   |
#### Ou exclusivo (XOR)
- Tabela verdade

| p   | XOR | q   |
| --- | --- | --- |
| V   | F   | V   |
| V   | V   | F   |
| F   | V   | V   |
| F   | F   | F   |
- Temos verdadeiro apenas quando uma das proposições são verdadeiras.
![[Pasted image 20251124211200.png]]

### Operadores Lógicos Avançados (Condicional e Bicondicional)

#### Condicional ( -> )
- Tabela verdade

| p   | ->  | q   |
| --- | --- | --- |
| V   | V   | V   |
| V   | F   | F   |
| F   | V   | V   |
| F   | V   | F   |
- Só é *falso* quando a 'promessa' não for comprida

#### Bicondicional
- Tabela verdade

| p   | <-> | q   |
| --- | --- | --- |
| V   | V   | V   |
| V   | F   | F   |
| F   | F   | V   |
| F   | V   | F   |
- O valor é *verdadeiro*, caso as duas preposições sejam falsas ou verdadeiras, mas caso uma delas seja falsa, o valor da bicondicional é falsa.

### Propriedades
- Dupla negação:
	- (p') '<-> p
- Leis idempotentes:
	- p + p <-> p
	- p . p <-> p
- Comutatividade:
	- p + q <-> p + q
	- p . q <-> q . p
- Leis associativas:
	- (p + q) + r <-> p + (q +r)