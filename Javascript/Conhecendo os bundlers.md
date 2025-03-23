___
### Bundlers
- *Agrupa (empacota)* diversos arquivos e suas dependências em um ou mais pacotes com o objetivo de otimizar o carregamento de páginas web.

### Funcionamento
- No geral, a operação de um empacotador é dividida em duas etapas:
- *Geração do gráfico de dependência*,
- *Empacotamento*

### Mapeando um gráfico de dependência
1. A primeira coisa que um empacotar de módulo faz é gerar um mapa de relacionamento de todos os arquivos servidos. Este processo é denominado *Resolução de Dependências*.
2. O empacotador requer um arquivo de entrada (geralmente o arquivo principal). Em seguida analisa o arquivo de entrada para entender suas dependências.
3. Depois disso, ele percorre as dependências para determinar as dependências dessas dependências.

### Agrupamento
- Depois de receber entradas e passar por suas dependências durante a fase de Resolução de Dependências, um bundler entrega *ativos estáticos* que o navegador pode processar com êxito.
- Este estágio de saída é denominado *Packing*. Durante esse processo, o empacotador aproveitará a resolução de dependência para integrar nossos vários arquivos de código e retornar um único pacote para o navegador carregar.