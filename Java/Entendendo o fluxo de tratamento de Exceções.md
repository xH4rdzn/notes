___
### O que são exceções ?
- São eventos que ocorrem durante a execução de um programa que indicam a ocorrência de um erro ou uma condição inesperada.

### Por que devemos tratar as Exceções ?
- Tratando exceções de maneira adequada, poderemos fornecer mensagens de erro mais compreensíveis e amigáveis em nossa API.

### Utilizando a RFC Problem Details
- O padrão Problem Details é um formato específico definido pera **RFC 7807** que oferece uma estrutura consistente para comunicar problemas de maneira detalhada e compreensível.

#### Padrão de retorno da ***RFC Problem Details (7807)***
- `Type`-> Esta URI deve fornecer um link para uma documentação legível (em HTML) para humanos sobre o tipo de problema. Caso não tenha, deveremos retornar ***`about:blank`***;
- `Title` -> Um resumo curto e legível para humanos do tipo de problema;
- `Detail` -> Uma explicação legível para humanos, específica para esta ocorrência do problema.
- `Status` -> O código de status HTTP gerado pelo servidor de origem para esta ocorrência do problema.
- `Instance` -> Uma referência URI que identifica a ocorrência específica do problema.
- Podemos incluir mais campos customizados para enriquecer a informação do erro. Ex: invalid-params, etc;

### Quais são as formas de tratamento de Exceções ?
- O Spring fornece um mecanismo para capturar e converter as exceções de seu projeto para um retorno amigável na API com Problem Detail.
- Podemos tratar as exceções de forma específica nas controladoras. ***`@ExceptionHandler`***
- Podemos tratar exceções de forma global para toda a aplicação ***`@RestControllerAdvice + @ExceptionHandler`***;