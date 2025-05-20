___

### Visão Geral
- Um programa de computador em execução lida com dados.
- Esses dados são armazenados em *variáveis*

### Variáveis
- Em programação, uma variável é uma porção de memória (RAM) utilizada para armazenar dados durante a execução dos programas.

#### Declaração de variáveis
- **Sintaxe**:
```text
<tipo> <nome da variável> = <valor inicial>;
```
- **Exemplos**:
```java
int idade = 25;

double altura = 1.68;

char sexo = 'F';
```
- `int`-> armazena valores inteiros.
- `double` -> armazena valores de ponto flutuante.
- `char`-> representa apenas um caractere;

### Tipos primitivos em Java

| Descrição                           | Tipo    | Tamanho | Valores             | Valor Padrão |
| ----------------------------------- | ------- | ------- | ------------------- | ------------ |
| Tipos numéricos inteiros            | byte    | 8 bits  | -128 a 127          | 0            |
| Tipos numéricos inteiros            | short   | 16 bits | -32768 a 32767      | 0            |
| Tipos numéricos inteiros            | int     | 32 bits |                     | 0            |
| Tipos numéricos inteiros            | long    | 64 bits |                     | 0L           |
| tipos numéricos com ponto flutuante | float   | 32 bits |                     | 0.0f         |
| tipos numéricos com ponto flutuante | double  | 64 bits |                     | 0.0          |
| um caractere Unicode                | char    | 16bits  | '\u0000' a '\uFFFF' | '\u0000'     |
| valor verdade                       | boolean | 1 bit   | { false, true}      | false        |
- Um bit pode armazenar 2 valores possíveis (*0 ou 1*)
- Cada bit = 2 possibilidades
- 8 bits: 256 possibilidades
- Ainda existe o tipo `String`que é uma cadeia de caracteres.

### Nomes de variáveis
- Não pode começar com dígito: use uma letra ou _
- Não pode ter espaço em branco
- Não usar acentos ou til
- Normalmente usamos o padrão 'camelCase'
```java
// Exemplos Corretos
int _5minutos;

int salario;

int salarioDoFuncionario;
```