___

### Estrutura de Diretórios do Linux
##### Diretório Raiz
- Barra /
- Equivalente ao `C:\` no Windows
- Onde todos os outros diretórios estão colocados
##### Diretório *bin*
- /bin
- *Binaries (binários)*
- Onde se encontram-se os binários (executáveis) de diversos programas
- Shell scripts
		- Similares aos arquivos de programas do windows. A diferença é que aqui estão somente os executáveis.
##### Diretório boot
- /boot
	- Contém os arquivos necessários para seu Sistema Operacional inicializar
	- Contém o *GRUB*, por exemplo
##### Diretório dev
- /dev
- Devices (dispositivos)
- Onde encontram-se os arquivos do seu hardware. Discos, som, câmera etc.
- Unidades de disco são chamadas de:
	- /dev/sda1 ou /dev/sda2
	- O número no final varia de acordo com a partição
##### Diretório etc
- /etc
- Et cetera
- Mantém as configurações gerais do sistema para todos os usuários
##### Diretório home
- /home
- Mantém os arquivos e configurações do usuários do sistema
- Similar ao Users/Usuários do Windows
##### Diretório root
- /root
- Mantém os arquivos e configurações do root do sistema (administrador)
##### Diretório lib
- /lib
- Library (biblioteca)
- Mantém bibliotecas usadas por softwares
- Similar a *DLL* em ambiente Windows
##### Diretório media
- /media
- Local de montagem de discos removíveis automáticos.
##### Diretório mmt
- /mnt
- Mount (montar)
- Local de montagem de discos manuais pelo usuário
##### Diretório opt
- /opt
- Optional (opcional)
- Diretório usado por alguns fabricantes para instalar seus softwares
- O Google Chrome é um exemplo de software que fica por padrão nessa pasta
#### Outros diretórios
- /proc
	- Mantém arquivos sobre o sistema e seus processos
- /run
	- Armazena informações e logs de serviços que rodaram
- /sbin
	- Semelhante ao *bin*, mas são binárois que só podem ser acessados pelo *root*
- /temp
	- Diretório de arquivos temporários de cada sessão
- /usr
	- Já foi a pasta de usuários
	- Hoje, mantém arquivos de programas para usuários
- /var
	- Arquivos como *logs* do sistema, backups, ou seja, arquivos de tamanhos variáveis e que tendem a crescer de tamanho