___
#### O que são Containers
- Um container é um padrão de unidade de software que empacota código e todas as dependências de uma aplicação fazendo que a mesma seja executada rapidamente de forma confiável de um ambiente computacional para o outro. - *Definição no Site do Docker*
- Mas isso é uma definição genérica;

#### Como funciona os Containers
- Com o passar da evolução dos sistemas operacionais, e seus processos, eles no possibilitaram de trabalhar com *namespaces*;
- Os *namespaces* é uma forma de isolar os processos;
- Então quando falamos de containers, estamos falando em um processo que é isolado com processos filhos;
- *Pid* -> são os números dos processos;
- *User* -> Com os *namespaces*, conseguimos fazer a separação baseados dentro dele;
- *Network* -> Conseguimos fazer o isolamento de rede
- *File System* -> Conseguimos trabalhar com sistemas de arquivos;
- No final das contas um container é um processo com sub-processos, rodando que emulam um sistema operacional;
- Além dos *namespaces*, temos o *Cgroups*, que foi criado pelo `Google`;
- Os *Cgroups*, fazem o controle dos recursos computacionais do container;
- A ideia do *Cgroups* então é isolar os recursos computacionais dos processos do container, podemos definir os recursos que este container vai poder utilizar;
- E o terceiro pilar, para trabalhar com containers é o *File System*;
- Os *File System* dos containers, principalmente do Docker, trabalhamos com o `OFS - (Overlay File System)`;
- A grande ideia do `OFS`, é trabalhar com camadas (`layers`), essas camadas trabalham de forma individualizada.
- Um container não possui um sistema operacional inteiro dentro dele, ele só possui os pedaços que precisa para funcionar;
- Uma imagem é um conjunto de dependências encadeadas em uma arvore, para podermos utilizar; 
#### Dockerfile
- É um arquivo declarativo, onde escrevemos como vai ser a imagem que vamos `buildar`;
- A imagem principal é sempre uma *imagem em branco*, mas normalmente nunca partimos da *imagem em branco*;
```dockerfile
FROM: ImageName
```
- O `FROM`, passamos o nome da imagem, ao rodarmos o `Dockerfile`, ele vai baixar automaticamente toda essa imagem e suas dependências; 
- Temos a opção de customizar essa imagem, podemos rodar alguns comando nessa imagem, para isso utilizamos o `RUN`
```DOCKERFILE
FROM: ImageName
RUN apt-get-install
```
- Através do `Dockerfile`, também podemos expor portas especificas dessa imagem, para podermos ter acesso
```Dockerfile
EXPOSE 8080
```
- Olhando isoladamente para o processo no qual roda o nosso container, neles vamos ter:
	- *Image* -> Essa imagem é imutável;
	- Quando subimos essa imagem é criada uma camada que chamamos de `Read/Write`, essa camada conseguimos escrever e fazer alterações no container que está rodando, **estamos fazendo alterações no container e não na imagem**;
- Então a partir do nosso `Dockerfile`, construímos uma `Image`, e todas as `Images`, tem uma camada de `Read/Write`;
- Então toda vez que um `Dockerfile` roda é gerada uma nova imagem;
- Mas é possível fazer um `commit`, tudo que estava no container que estava rodando vai para a nova imagem;
- As imagens ficam no `Image Registry`, é como um repositório de imagens;

#### Como o Docker funciona ?
- Juntando os 3 pilares -> *Namespaces, Cgroups e o File System*, o Docker conseguiu criar um conceito que é chamado de **Docker Host**;
- O `Docker Host`, esse host fica rodando um processo que é chamado de `daemon`, que fica disponibilizando uma `API`;
- Mas para falarmos com o `Docker Host`, precisamos do `Docker Client` que fazem as chamadas para a `API`, do `Docker Host`;
- O `Docker Host`, possui um `Cache`, ele armazena as imagens que vem do `Image Registry`, assim ele não precisa ficar fazendo download toda hora;
- O `Docker Host`, possui também um gerenciador de volumes, como sabemos que as imagens são imutáveis, então para fazermos uma persistência de dados, fazemos o uso dos `volumes`;
- O Docker também, possui uma parte de `Network`, essa camada possibilita a comunicação entre os containers;