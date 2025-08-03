___

### O Linux
- O *Linux* é um sistema operacional;
- **Linus Torvalds**. Helsinki, Finlândia.
- Em 1991. Baseando-se no *Unix*, escreveu o seu próprio *Kernel*, que ficou conhecido como ***Kernel Linux***;
- Graças a divulgação do código por Linus, muitos desenvolvedores ao redor do mundo contribuíram com o projeto, tornando o Linux possível.
- Tux é o pinguim mascote do Linux;
 ![[Pasted image 20250722205551.jpg]]
- **1992** -> Linux é disponibilizado sob a *Licença Pública Geral (GPL)*, criada por **Richard Stallman**
- Tornou possível a criação de uma vasta comunidade de desenvolvedores Linux. Sempre propondo atualizações no *Kernel* e possibilitando o uso de outros componentes **GNU** para o sistema operacional.
- A integração do *Kernel Linux* com outros componentes e softwares gerou o que chamamos e *distribuições Linux*.
- **1998** -> Grandes empresas como IBM e Oracle anunciaram seu suporte ao Linux, expandindo as aplicações e o mercado Linux como um todo
- O *Kernel* é o núcleo do sistema operacional, e é responsável por:
	- Principais funções do sistema operacional
	- Gerencia de recursos (memória e CPU)
	- Abstrair o hardware (prover drivers)
	- Prover sistemas de arquivos e proteção.
- O *projeto GNU*:
- **1983** -> Richard Stallman idealizou o projeto que tinha como objetivo criar um sistema operacional de software livre.
- **1992** -> O projeto GNU havia criado todos os componentes principais do sistema operacional, exceto o *kernel*.
- Se juntarmos o Kernel Linux com o GNU, temos um sistema operacional completo e de software livre.
- Nem todo *Kernel* de Linux trabalha com componentes GNU. Porém, os que trabalham, são também conhecidos como sistemas ***GNU/Linux***;
- O Linux e o projeto GNU tem o mesmo objetivo: desenvolver *softwares* totalmente *livres*.
- Em que termo livre se refere à *liberdade*, e não a preço
	- A liberdade de usar o software para qualquer propósito
	- A liberdade de adaptar o software para atender a nossa necessidade
	- A liberdade de compartilhar o software com quem desejarmos
	- A liberdade de compartilhar as mudanças que fizermos nele.
- *Linux Foundation* e *Free Software Foundation (FSF)* é a organização que patrocina o projeto GNU.

### Licenças de software
- Softwares estão protegidos por direitos autorais, como qualquer outra propriedade intelectual.
- É um contrato entre quem desenvolve e quem consome o software
- Define a usabilidade de um software por parte do usuário
- Restrição de cópia, distribuição e adaptações.
- A nível de desenvolvedor, definem como o código-fonte pode ser utilizado e manipulado
#### Software Livre
- Estabelecido pela *Free Software Foundation*.
- Liberdade de alterar, adaptar e redistribuir cópias com modificações.
	- Linux, GIMP, Mozilla Firefox
#### Open Source
- Similar a um software Livre
- A diferença é que quem determina as condições de uso e distribuição é o desenvolvedor original. Enquanto que o software livre deve sempre permanecer livre a cada nova redistribuição.
#### Copyleft
- Copyleft
	- Liberdade de modificação e distribuição garantidas
	- Um software deve ser alterado e redistribuído pelas mesmas condições em que obteve (mesma licença).
#### GNU General Public License (GPL) v2
- Licença de software para software idealizada por *Richard Matthew Stallman*
- Princípio de liberdade
- Licença Copyleft
- Linux e GNU
#### Software Gratuito (freeware)
- Seu uso não implica em pagamento de nenhuma maneira.
- Restrições podem existir, como o software ser destinado somete a uso acadêmico, por exemplo.
#### Shareware
- Software também gratuito, mas com limites para experimentação.
	- Tempo, funcionalidade, etc...
#### Software proprietário
- É proibida a cópia, alteração ou redistribuição.
- O descumprimento do contrato pode impactar em ações judiciais
	- Windows, Adobe Photoshop, Office, etc..
#### Software as a Service (SAAS)
- Software remotos em que você não compra uma licença, mas sim usa o software por meio de uma conexão com a internet.
	- Netflix, Spotify, Office 365

### Distribuições Linux

#### Debian
- Voltada para estabilidade e segurança
- Interface padrão: *GNOME*
- Variações: Ubuntu, Kurumin, Raspbian.
#### Ubuntu
- 2004. Baseado no Debian. Não-comercial e mantido pela empresa sul-africana *Canonical*;
- Muito popular. De fácil uso e com muitos materiais na Internet.
- Tarefas administrativas com *sudo*
- Gerenciador de pacotes: apt (.deb);
#### Mint
- Baseado no Debian/Unbutu

#### Red Hat
- Baseado no *Fedora*. Comercial com foco no mercado corporativo
- Hoje pertence a IBM
- Primeira distro a usar um sistema de gerenciamento de pacotes.
- Gerenciador: dnf(.rpm).

### Terminologia Linux
- O meio *Linux* é bastante vasto e tem uma terminologia própria.
- Já aprendemos alguns destes termos, como:
	- Kernel, distribuição e GNU.
##### Boot loader
- é o programa que realiza a inicialização do sistema operacional.
- Exemplos: *GRUB, LILO, ISOLINUX*;
##### Processo de inicialização
**POWER ON** -> **BIOS** -> **MBR** -> **Boot Loader** -> **Kernel Linux**;
##### Sistemas de arquivos
- Maneira de organizar e armazenar arquivos no sistema operacional
- Exemplos: FAT, NTFS, ext3, ext4, BtrFS
##### X Window System
- Kit de ferramentas e protocolos para construção da interface gráfica ao usuário
- Está sendo aos poucos substituido pelo *Wayland*, que é o mais otimizado.
##### Linha de comando (terminal)
- Interface para inserir comandos no sistema operacional.
##### Shell
- Interpretador de linhas de comando e instruções do sistema para realizar tarefas
- Exemplos: bash, tcsh, zsh;

### Serviços no Linux e certificações

#### Serviços
- É um programa que roda como um processo em background.
- Exemplos: Libre Office, GIMP, VLC Player etc.
#### Certificações
- Oportunidade de se destacar no mercado.
- Gera profissionais capacitados
