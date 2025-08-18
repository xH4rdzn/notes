___
### Software, programas e sistemas
- Software consiste em:
	1. *Instruções* (programas de computador) que, quando executadas, fornecem características, funções e desempenho desejados
	2. Estruturas de dados que possibilitam aos programas manipular informações adequadamente
	3. Informação descritiva, tanto na forma impressa quanto na virtual, descrevendo a operação e o uso dos programas
- Software -> um programa de computador e toda documentação associada a ele.
	- Programa
		- Sequência de passos ou instruções descritos por um *algoritmo*
	- Algoritmo
		- Estrutura passo a passo de como um problema deve ser resolvido.
		- Exemplo: *uma receita de bolo*
- Software de Sistema (Básico)
	- Sistemas Operacionais
	- Sistemas tradutores
	- Software Utilitário
- Software Aplicativo
###### Software de Sistema (Básico)
- Coleção de programas para apoiar outros programas
- Sistema Operacional
- Softwares utilitários ou ferramentas de sistemas
- Exemplos: *Android*, *Ubuntu*, *MacOS*;
###### Software utilitário
- Fornecem ao usuário ferramentas para organizar os discos, verificar disponibilidade de memória, corrigir falhas de processamento.
- Úteis ao sistema computacional
- Exemplos: *Anti-Vírus*, *compactadores*, *emuladores*, *desfragmentadores*, *formatadores*, *backup*;

### Sistema Operacional
- Sistema -> Conjunto de partes que se interagem para alcançar determinado objetivo.
- O que diferencia software de sistema é *que um sistema pode ser definido como um conjunto de softwares* que interagem entre si para alcançar determinado objetivo.
- O software básico é aquele necessário para o funcionamento do hardware ou de parte dele.
	- Exemplos: Sistemas Operacionais (Windows, MacOS, Linux) e Sistemas Tradutores.
- O sistema Operacional é o software responsável pela supervisão dos processos executados em um computador.
- Gerencia todo o hardware e todo o software do computador e realiza a **comunicação** entre eles.
- Podemos falar que o sistema operacional é uma camada de software entre o hardware e os softwares usados pelo usuários.
- As funções do *Sistema Operacional*:
	- Facilitar o uso do computador pelo usuário, tornando mais simples a utilização de seus recursos.
	- Gerenciar os recursos do computador
	- Controlar a execução de programas pela **CPU**
##### Sistemas Tradutores
- Converte os programas escritos para um código em uma linguagem de máquina, mais adequada para manipular *bits*;
- Programa escrito em linguagem de alto nível: necessidade de ser traduzido para a linguagem de máquina para que o computador possa executá-lo

### Algoritmos e Linguagens

##### Algoritmo

> "Algoritmo é uma sequência de passos que visa atingir um objetivo bem definido." - Forbellone, 1999
- Objetivo: representar mais fielmente o raciocínio envolvido na lógica de programação
- Uma vez concebida uma solução, esta pode ser traduzida para qualquer linguagem de programação.
###### Sintaxe x Semântica
- Gap semântico entre lógica de programação e a lógica do dia a dia
- Semântica na linguagem de programação: referindo ao conteúdo, ao significado
- Sintaxe está relacionada com as regras, premissas, restrições
- Modo como as palavras podem ser combinadas e formar os enunciados define a sintaxe.
###### Semântica
- Define o significado formal das expressões, comandos ou unidades de programas
- Erros de semântica estão relacionados a lógica de programação.
- Exemplo: expressão sintaticamente correta na linguagem *Python*, mas semanticamente não faz sentido somar um número e um caractere
```python
a = 2 + "3"
```

##### Linguagens
- Linguagens de programação tratam os dados de um computador por meio do uso de algoritmos
- Programador:
	- Deve encontrar um algoritmo que resolve o seu problema
	- Implementá-lo usando uma linguagem de programação;

#### Glossário do desenvolvedor de software
- *Front-end* -> parte gráfica de uma aplicação web
- *Back-end* -> desenvolvimento no lado do servidor
- *Full-stack* -> ambas as abordagens
- *API* -> Application Programming Interface
	- Conjunto de rotinas e padrões de programação
	- Objetivo -> acessar aplicativos de software
	- Plataformas baseados na web
	- Utilizada por programa/aplicação
- *Framework*:
	- Conjunto de código de LP específica
	- Auxilia no desenvolvimento web ou de software
	- Biblioteca de códigos com funções já prontas
	- Arcabouço de código
- *IDE* -> Integrated Development Environment
	- Integra diversas funcionalidades para desenvolvimento em única interface gráfica
	- Auxilia e agiliza o processo de desenvolvimento
- *SDK* -> Software Development Kit
	- Composição: compilador, debugger e API
	- Conjunto de ferramentas fornecidas por um fabricante para que se desenvolva para uma plataforma ou sistema especifico
- *Nativo*
	- Desenvolvido para uma única plataforma
	- Utilização de linguagens e ferramentas específicas para a plataforma em questão
- *Híbrido*
	- Implementação utiliza html, css e Javascript
	- Frameworks ou ferramentas que permitem uma mesma base de código
	- Uma linguagem e distribuída para várias plataformas
- *Serviços*
	- Processos de software
- *Monolítico* -> roda com um único processo
- *Microserviços* -> abordagem arquitetônica e organizacional do desenvolvimento de software na qual o software consiste em pequenos serviços independentes que se comunicam usando APIs bem definidas. São autônomos e especializados.
- *SOAP* -> Service Oriented Architecture
	- Utiliza arquivos xml
	- Protocolo de transporte: HTTP
- *REST* -> Representational State Transfer
	- Conjunto de restrições para criação de webservices
	- Quando um serviço implementa esse padrão: Restfull
	- Restfull utiliza arquivos *JSON*
- *COMMIT*
	- Enviar alterações de determinado trecho do código
	- Enviar criação de uma nova versão do projeto
- *VERSIONAMENTO*
	- Atribuição de número de versão ao estado do projeto;
- *SNAPSHOT*
	- Cópia instantânea em determinado tempo de um volume
- *DEBUG*
	- Debugging ou debugar
	- Depurar o programa
	- Encontrar erros no programa e tentar resolvê-los
- *GIT*
	- Sistema de controle de versão
	- Gerencia as várias versões no desenvolvimento de um documento
	- O logo do *GIT* representa a ramificação para o desenvolvimento não linear
- *GITHUB*
	- Plataforma de desenvolvedor completa para criar, dimensionar e fornecer software seguro
	- Utiliza *GIT* como sistema de controle

#### Ciclo de vida de desenvolvimento de softwares
- Software Development Life Cycle - SDLC
- Modelo de processo
- Representação simplificada de um processo de software
- Quatro atividades são comuns a todos os processos de software:
	- Especificação
	- Desenvolvimento
	- Validação
	- Evolução
###### Metodologia Ágil
- Alternativa para gestão de projetos tradicionais
- Entrega rápida das funcionalidades
- Foco no software e não no projeto
- Adequada a aplicações em que os requisitos mudam rapidamente
- Duas abordagens: o extreme Programming(XP) e o SCRUM