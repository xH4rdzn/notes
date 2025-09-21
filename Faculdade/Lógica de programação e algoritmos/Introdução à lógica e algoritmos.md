___

### O que é lógica ?
- **Aristóteles** (384 a 322 a.C.) - conceito de lógica (logos) - linguagem racional;
- Parte de filosofia que se ocupa das formas do pensamento e das operações intelectuais (**Michaelis, 2020**)
- **Raciocínio lógica** do nosso dia a dia para realizar atividades.
- Na *computação*: maneira pela qual instruções, assertivas e pressupostos são organizados num algoritmo para viabilizar a implantação de um programa (**Michaelis, 2020**);

### O que são algoritmos ?
- Um algoritmo é dado como uma sequência de passos a serem realizados para que determinada tarefa seja concluída, ou um objetivo atingido;
- Abaixo temos um exemplo de algoritmo:
```text
- Pegue uma fatia de pão de forma
- Com a ponta da faca, raspe duas vezes na manteiga dentro do pote
- Com a mesma faca que contém a manteiga, espalhe uniformemente a manteiga em um dos lados do pão de forma
- No mesmo lado que você espalhou a manteiga, coloque uma fatia de queijo e uma de presunto, esta última em cima da de queijo
- Em cima das fatias, coloque o outro pão de forma e pronto, seu sanduíche está finalizado 
```

### Sistemas de computação
- Segunda Guerra Mundial:
	- Cálculo de mísseis
	- Mensagens codificadas
	- Computadores construídos com milhares de válvulas e relés, pesando toneladas e consumindo montantes gigantes de energia elétrica
- Um exemplo desses computadores é o **ENIAC** (Electronic Numerical Integrator and Computer);
- Percebeu-se a necessidade de mudar a maneira como computadores eram projetados, começando pela aritmética decimal para binária.
- ***John von Neumann*** - matemático húngaro. Propôs o primeiro computador de programa armazenado e criado
![[Pasted image 20250921111139.png]]
- Unidade de controle e Unidade de lógica e aritmética, esses dois blocos juntos formam o *Unidade Central de Processamento*, que é o processador;
- Todo e qualquer computador é binário
- ***Binary digit*** - a menor unidade de armazenamento de dados
- ***Palavra (word)*** - a menor unidade útil de manipulação do dado

#### O Sistema Operacional
- Define quais softwares e quando serão executados
- Gerencia o uso de memória
- Abstrai o hardware para o usuário e para o desenvolvedor

### Representação de algoritmos

##### Descrição Narrativa
- Linguagem Natural
- Não utilizada em algoritmos computacionais
```text
- Ler dois valores (x e y)
- Verificar se x e y são iguais
- Se x for igual a y, mostrar a mensagem "Valores Iguais!"
- Se x for diferente de y, mostrar a mensagem "Valores diferentes!"
- Fim          
```
##### Pseudocódigo
- Português estruturado
- Representação mais próxima de um programa computacional, mas sem se preocupar com a linguagem de programação adotada
- Regras definidas
- Linguagem genérica
```portugol
Algoritmo - exemplo
Var
	x,y: inteiro
Início
	Ler(x, y)
	Se (x = y) então
		Mostrar("Valores iguais!")
	Senão
		Mostrar ("Valores diferentes!")
	Fimse
Fim			
```
##### Fluxograma
- Representação gráfica de um algoritmo
- Usado para passar a ideia do seu código e organizar o raciocínio lógico
- Simbologia gráfica padrão ISO 5807:1985

### Linguagens de programação e compiladores
- Um computador só compreende bits

##### Linguagens de programação
- Uma linguagem de programação é portanto, esse conjunto de regras, com palavras-chaves, verbos, símbolos e sequências específicas. Chamamos todo esse conjunto de *sintaxe da linguagem*
- Resultam em instruções compreendidas pelo computador e não geram ambiguidades.
##### Software de compilação
- Se o computador compreende uma linguagem e você trabalha em outra, diferente e ilegível para ele, como o computador entende o código que você fez ?
- Ele transforma o código que você escreveu (alto nível) em uma linguagem de máquina(baixo nível) compreendida pelo hardware
- *Compilador* - transforma um código-fonte em um arquivo binário
- *Interpretador* - o código não é convertido de uma só vez, mas, sim, executado instrução por instrução à medida que o programa vai requisitando