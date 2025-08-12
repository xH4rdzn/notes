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
### Comandos de Manipulação de Diretórios

#### Comando *ls*
- Lista o conteúdo de um diretório
```zsh
ls
```
- Podemos por opções como:
- -A -> inclui os arquivos com o nome iniciando com '.' na listagem (arquivos ocultos);
- -R -> Lista recursivamente os diretórios encontrados
- -d -> Lista nomes de diretórios como arquivo preferencialmente no lugar de seus conteúdos.
#### Comando *cd*
- Muda o diretório corrente para 'dir'
```zsh
cd 
```
- ~ -> vai direto para a home do usuário
- .. -> Retorna para o diretório anterior
- -L -> Segue links simbólicos
- -P -> Usa a estrutura física de diretórios em vez de seguir links simbólicos
#### Comando *mkdir*
- Criar diretórios
```zsh
mkdir nomeDaPasta
```
- -p -> Cria os diretórios-pai de um caminho, caso eles não existam ainda
- -m -> indica o modo - permissões de um diretório no momento de sua criação.
#### Comando *rmdir*
- Remover diretórios vazios
```zsh
rmdir nomeDaPasta
```

#### Comando *rm*
- Remove diretórios ou arquivos
```zsh
rm -r nomeDaPasta
```
- -i -> Questiona se cada arquivo será apagado. Se a resposta for negativa, o arquivo é preservado.
- -r -> Apaga o conteúdo dos diretórios de forma recursiva
- -R -> igual a -r;

#### Comando *pwd*
- Esse comando mostra o caminho no qual estamos.
```zsh
pwd
```

### Comandos de Gerenciamento de Pacotes

#### Comando *apt*
- Instala e atualiza pacotes/programas
```zsh
sudo apt update
```
- Localiza todos os pacotes a serem atualizados

##### apt list nomePacote
- Descobre se o pacote está instalado ou não e a sua versão

### Comandos de Processos
- Todos os programas em execução podem ser chamados de processos e são identificados por um número chamado **PID** (process identication)
- Os processos podem estar em três estados diferentes: em *foreground (primeiro plano)*, em *background (segundo plano)* ou suspensos
- Os processos em *foreground* costumam segurar o controle do terminal até encerrarem
- Podemos mandar o processo para *background* para não deter o controle do terminal;
##### Comando ps
- Retorna uma lista dos processos em execução
```zsh
ps
```
- -a -> busca todos os processos no sistema
- -x -> lista todos os processos pertencentes ao usuário
- -u -> mostra o nome de usuário que iniciou o processo e hora em que o processo foi iniciado.
##### Comando *top*
- Mostra os programas em execução ativos, parados, uso de CPU, memória RAM, Swap etc.
- Continua em execução mostrando continuamente os processos que estão rodando em seu computador e os recursos utilizados por eles
```zsh
top
```
##### Comando *jobs*
- O comando *jobs* mostra os processos que estão parados ou rodando em segundo plano
- Processos em segundo plano são iniciados usando o símbolo `&`no final da linha de comando
```zsh
jobs
```
##### Comandos *fg* e *bg*
- O comando *fg* coloca um processo em *foreground*
```zsh
fg PID
```
- O comando *bg*, coloca um processo em *background*
```zsh
bg PID
```
##### Comando *kill*
- Encerra um processo em execução
```Zsh
kill PID
```

### Comandos de Acesso e Permissões
- As permissões de acesso existem para proteger o sistema de arquivos de acessos indevidos de pessoas ou programas não autorizados
##### Dono
- É quem criou arquivo ou diretório. É o mesmo nome do usuário que estiver logado no sistema
- A identificação do dono também é chamada de *user id* (uid);
##### Grupo
- Permite que vários usuários diferentes tenham acesso a um mesmo arquivo.
- A identificação do grupo é chamada de *group id* (GID);
##### Tipos de permissões
- r- -> permissão de leitura para arquivos. Para diretórios, permite listar seu conteúdo;
- w- -> permissão de escrita para arquivos. Para diretórios, permite a gravação de arquivos
	- Um arquivo/diretório só pode ser apagado se tiver permissão de escrita
- x- -> permite executar um arquivo(caso seja um programa executável). Para diretórios, permite que seja acessado através do comando `cd`;
##### Exemplo
```zsh
-rwxr-xr-- igor users nomeArquivo
```
- 1º caractere - diz o tipo do arquivo. Um `d`é um diretório; um `l`, um link para um arquivo no sistema; um `-`é um arquivo comum
- 2-4º caractere - permissões do dono do arquivo;
- 5-7º caractere - permissões do grupo do arquivo (*users*)
- 8-10º caractere - permissões de outros usuários ao arquivo
##### O *root*
- O usuário *root* não tem nenhuma restrição de acesso ao sistema.
- A conta *root* somente deve ser usada para fazer a administração do sistema. Além disso, deve ser usada o menor tempo possível
- Utilize uma conta de usuário normal em vez da conta *root* para operar o sistema;
##### Comando *chmod*
- Modifica as permissões de um arquivo ou diretório
```zsh
chmod [opções] [permissões] [diretório/arquivo]
```