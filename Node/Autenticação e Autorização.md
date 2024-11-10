___
- Autenticação -> Quem você é ? (Identificação)
- Autorização -> O que você pode fazer ? (Permissão)
#### Autenticação
- A autenticação é o processo de verificar a identidade de um usuário. É como provar que a pessoa é quem ela diz ser.

##### Fluxo de Autenticação
- Quando um usuário faz login em uma aplicação, ele fornece credenciais (como e-mail e senha) que são verificadas. Se as credenciais forem válidas, o usuário será considerado autenticado.
- O cliente faz a solicitação de autenticação com e-mail e senha, para o Back-end, o Back-end verifica se no banco de dados esse usuário existe e as credenciais, se os dados forem válidos, ele retorna o token de autenticação, caso contrário ele retorna e-mail e/ou senha inválido;

#### Autorização
- A autorização define o que um usuário autenticado pode ou não fazer dentro do sistema. Depois de identificado, o sistema verifica quais permissões o usuário tem.

##### Fluxo de autorização
- Um usuário pode estar autenticado no sistema, mas ainda assim não ter permissão para acessar um painel administrativo ou excluir dados. A autorização determina esse nível de acesso com base no papel (role) ou permissões atribuídas ao usuário.

