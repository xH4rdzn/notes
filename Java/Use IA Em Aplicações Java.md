___
## Produtividade com ferramentas de IA para desenvolvedores

#### O papel evolutivo da IA
- A IA está transitando de uma ferramenta de assistência para um parceiro de desenvolvimento.
- Essa relação combina a intuição e o julgamento humano com a precisão e a capacidade computacional da máquina, gerando potenciais de resultados superiores aos que poderíamos alcançar até então
#### Ganhos de produtividade mensuráveis
- Performace geral: até 2x mais rápido em tarefas comuns.
- Por tipo de tarefa:
	- Documentação: cerca de 50% do tempo.
	- Escrever código novo: quase 50% do tempo.
	- Refatoração: ~66% do tempo original.
- *Complexidade alta: economia < 10%*
- *Experiência do dev júnior (<1 ano): 7% a 10% mais lento com ***GenAI**
- Entrega no prazo: 25% a 30% de aumento de probabilidade.
- Qualidade do código: leve melhora (menos bugs, melhor legibilidade e manutenibilidade) quando há iteração ativa com a ferramenta.
- Experiência do desenvolvedor: >2x propensão a relatar felicidade, sensação de fluxo e satisfação.
- Combinar ferramentas: usar duas (chat + IDE) melhora 1,5 a 2,5X versus usar apenas uma.

#### Velocidade vs. Qualidade
- Apesar dos ganhos de velocidade, o código gerado por IA pode introduzir vulnerabilidades críticas
- As falhas mais comuns incluem
	- Ausência de validação de entrada (levando a injeções de SQL e coisas do tipo)
	- Falhas de autenticação e autorização
	- Uso de credenciais hard-coded
	- Ou seja: a vibe do *vibe coding* só vai até a página dois...

#### Mudança de habilidades essenciais
- A automação de tarefas repetitivas libera os desenvolvedores seniores para se concentrarem em atividades de maior valor, como:
	- Definição da visão e estratégia do produto
	- Priorização de funcionalidades
	- Arquitetura de sistemas complexos
	- Validação crítica do código gerado pela IA

#### Trabalhando o "INNER LOOP": Geração e Refatoração

##### Assistentes de código: uma decisão estratégica
- A escolha de um assistente de IA envolve um *trade-off* entre:
	- Funcionalidades
	- Integração com o ecossistema
	- **Privacidade e controle de dados**

##### Amazon Q Developer
- Oferece assistência "service-aware", com recomendações de recursos AWS e visibilidade em tempo real de logs e permissões diretamente no IDE. Suas capacidades "agentes" automatizam tarefas complexas como a crição de testes unitários, documentação e revisões de código
- *Prós*: Integração profunda com o ecossistema AWS, automação de tarefas expecíficas da AWS, varredura de segurança e controles de acesso corporativos
- *Contras*: Menos eficaz em projetos que não sejam AWS

##### Tabnine
- Foco em privacidade com uma política de retenção zero de dados e a capacidade de treinar modelos customizados com o código da empresa. Oferece agentes de IA especializados para a validação de requisitos, explicação de código e geração de documentação.
- *Prós:* Opções on-premise, personalizável com o código da equipe, amplo suporte a linguagens e modo offline.
- *Contras:* Pode consumir muitos recursos, qualidade das sugestões pode apresentar inconsistências.

##### Cursor
- Construído com um fork do **VS Code**, o Cursor é um editor de código projetado em torno da IA
- *Prós:* Experiência de IA profundamente integrada, excelente compreensão de todo o cdebase, refatoração rápida multi-arquivo e fortes opções de privacidade
- *Contras*:

##### JETBRAINS AI ASSISTANT
- Ferramentas de IA podem executar refatorações complexas, como extrair lógica repetida para funções reutilizáveis, converter laços imperativos em construções funcionais, e identificar e remover código morto ou inalcançável.
- *Prós*: Integração nativa e profunda com IDEs da JetBrains, sugestões de refatoração com reconhecimento de contexto e geração de testes e documentação
- *Contras*: Funcionalidades principais estão atreladas aos modelos na nuvem da JetBrains, limitando o uso.

### OuterLoop

##### SONAR: AI CODE ASSURANCE

- O SonarQube evoluiu para além da análise tradicional com o "AI Code Assurance", um workflow para validar código gerado por IA.
- *Prós*: Garante a qualidade do código gerado por IA, oferece correções automáticas com AI CodeFix e se integra a pipelines de CI/CD para bloquear merges que não atendem aos padrões.
- *Contras*: A configuração inicial pode ser complexa, pode gerar falsos positivos que exigem ajuste fino.
##### SNYK POWERED BY DEEPCODE AI
- Treinado em milhões de repositórios para entender o fluxo de dados e o contexto do código. Isso permite detectar vulnerabilidades complexas em código gerado por IA e humano.
- *Prós*: Detecção precisa com baixa taxa de falsos positivos, correções automáticas que aceleram a remediação e integração profunda no IDE para feedback em tempo real.
- *Contras:* O preço pode ser elevado para equipes maiores, a interface pode ser complexa para gerenciar um grande volume de vulnerabilidades e o foco principal é segurança

##### DIFFBLUE COVER
- Treina um modelo para otimizar métricas de qualidade de teste. Um "Reward Model" pontua os testes gerados com base em análises estáticas, ensinando o agente a evitar "test smells" (anti-padrões) e a produzir testes sintaticamente corretos.
- *Prós*: Gera testes garantidos para compilar e rodar, opera de forma autônoma, ideal para código legado e mantém o código-fonte privado.
- *Contras*: Focado exclusivamente em Java, pode ter uma curva de aprendizado para otimização e o custo de licenciamento pode ser um fator limitante.

##### MINTLIFY
- Plataforma de documentação "AI-native" projetada para ser consumida tanto por humanos quanto por LLMs, utilizando IA em todo o ciclo de vida. Ela oferece m escritor com consciência de contexto para auxiliar na criação e manutenção do conteúdo, e um assistente de IA que transforma a documentação em uma experiência de conversação para os usuários finais.

### IA corporativa com Java e Langchain4j
- Diferenciar IA Preditiva de IA Generativa.
- Compreender um fundamento: o desenvolvedor Java como integrador de IA, não como um cientista de dados.
- Identificar os componentes do stack tecnológico: Quarkus, Langchain4j etc...

##### O mundo da IA: duas realidades distintas
- A inteligência artificial no ambiente corporativo se manifesta em duas vertentes principais, com propósitos e capacidades fundamentalmente diferentes
- IA Preditiva:
	- Tecnologia madura, baseada em modelos estatísticos e machine learning clássico.
	- Objetivo: Analisar dados históricos para prever resultados futuros ou classificar informações.
	- Saída: Estruturada (um número, uma categoria, uma probalidade). Ex: score de crédito, detecção de fraude.
- IA Generativa:
	- Tecnologia emergente projetada para criar conteúdo novo e original.
	- Base: Utiliza Large Language Models (LLMs) para gerar textos, imagens, música e código em resposta a um prompt.
	- Saída: Não estruturada e criativa. Abre possibilidades para automação de comunicação e desenvolvimento de software

#### O papel do desenvolvedor
- A transição da IA Preditiva para Generativa eleva o desenvolvedor de um mero consumidor de APIs para um arquiteto de sistemas cognitivos.
![[Pasted image 20250929202940.png]]
- IA Preditiva
	- O desenvolvedor invocava um endpoint e processava uma resposta estruturada, tratando  modelo como uma "caixa-preta".
- IA Generativa
	- O desafio é mais estratégico. O desenvolvedor precisa projetar todo o fluxo de "pensamento";

#### Apresentação da stack tecnológica
- Quarkus: O nosso runtime de aplicação. O Java "Supersônico e Subatômico", otimizado para ambientes nativos da nuvem.
- Langchain4j: O framework de orquestração de IA. A "cola" inteligente que conecta nossa aplicação Java aos LLMs.
- Ollama: O servidor de LLMs local. Permite a execução de modelos offline.
