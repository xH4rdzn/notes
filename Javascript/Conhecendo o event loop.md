___

### Características

###### *Single Threaded*
- Executa uma coisa por vez.

###### *No-blocking*
- Não trava o contexto da execução

###### *asynchronous*
- Por ser no-blocking precisa utilizar um paradigma assíncrono para lidar com a execução das coisas.

###### *concurrent*
- As tarefas que executam assincronamente concorrem uma com as outras pelo processamento.

### Concorrência e Event Loop
- O JavaScript possui *modelo de concorrência* baseado em um *event loop* responsável por gerenciar a execução de código assíncrono e evento em um *único thread*, permitindo que o Javascript seja *não bloqueante*