___
### O que é Docker ?
- O Docker é um sistema de virtualização *não convencional.*
#### Virtualização Convencional
- Em virtualizações convencionais temos um software instalado na *máquina Host*que irá *gerenciar as máquinas virtuais*(exemplos: VirtualBox, VMWare, Parallels e etc).
- *Para cada máquina virtual* temos uma instalação completa do Sistema Operacional que queremos virtualizar, além de ter o próprio hardware virtualizado.
- O `docker` usa uma abordagem diferente, ele utiliza o conceito de *container*;
#### Containers
- Proporciona um *ambiente isolado* com os recursos que a sua aplicação precisa para funcionar(como código, dependências e bibliotecas necessárias para executar a aplicação).

#### Isolamento
- `Kernel`: O kernel é o coração de um sistema operacional que faz a ponte entre o software e o hardware e controla processos, memória, dispositivos e chamadas do sistema.
- `CGroups`: é uma funcionalidade que controla e limita a alocação de recursos, tais como CPU, memória, etc. O objetivo é não deixar que um contêiner monopolize os recursos do host para ter um ambiente equilibrado.
- `Namespaces`: isola os recursos, ou seja, um container só *enxerga* os seus próprios processo e arquivos.

#### Por que utilizar Docker ?
- Resolve o famoso problema: *"Na minha máquina funciona"*.
- Com o Docker temos um container com a nossa aplicação. Esse container pode ser levado inteiro para o outro ambiente. Com isso não precisamos nos preocupar com pré-requisitos instalados no outro ambiente, versão do S.O., permissões, etc;
- Dessa forma minimizamos muito a divergência entre os ambientes.

#### Conceitos do Docker
- `Dockerfile` : Contém todas as informações necessárias para gerar a nossa imagem Docker
- `Imagem`: Contém as informações de um ambiente com tudo que a nossa aplicação precisa para executar, por exemplo, código, dependências e bibliotecas necessárias.
- `Container`: É a instância de uma imagem em execução. Ou seja, é o ambiente de uma imagem executando.
- `Máquina hospedeira(host)`: Pode ser uma máquina virtual rodando em uma máquina física como um servidor ou diretamente na máquina física como o nosso computador.