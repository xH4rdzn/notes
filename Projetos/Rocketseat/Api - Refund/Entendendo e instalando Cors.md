___
### Cors
- *CORS (Cross-Origin Resource Sharing)* é uma funcionalidade de segurança que permite que uma página web acesse recursos de outra origem.
- Utilizamos para deixar habilitado que um projeto `front-end`que esteja hospedado em outro servidor, consiga acessar a nossa *api* e conseguir consumir os recursos dela;

### Como funciona ?
- O *CORS* é ativado quando uma página tenta acessar recursos de uma origem diferente daquela que a serviu.
- O *CORS* adiciona cabeçalhos HTTP que informam ao navegador se deve permitir o acesso aos dados solicitados.
- Os cabeçalhos *CORS* incluem `Acess-Controll-Allow-Origin`, `Access-Control-Allow-Credentials`, entre outros.
- O servidor verifica o cabeçalho da origem atual e responde com os dados solicitados
- O navegador visualiza os cabeçalhos da solicitação de controle de acesso e compartilha os dados retornados com a aplicação cliente.
