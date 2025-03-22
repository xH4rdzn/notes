___
- Quando uma função é assíncrona é chamada, ela retorna uma *Promise*.
- Quando a função assíncrona retorna um valor, a Promise será *resolvida* com o valor retornado.
- Quando a função assíncrona lança uma exceção ou algum valor, a Promise será *rejeitada* com o valor lançado.
- Uma função assíncrona pode conter uma expressão *await*, que *pausa e execução* da função assíncrona e *espera pela resolução da Promise* passada, e depois retoma a execução da função assíncrona e retorna o valor resolvido.