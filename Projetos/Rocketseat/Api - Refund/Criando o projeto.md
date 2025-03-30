___
- Com o terminal aberto, navegamos até a pasta onde queremos criar o nosso projeto, como no exemplo abaixo:
```zsh
cd projects
```
- Chegando na pasta desejada, podemos criar uma nova pasta para o nosso novo projeto:
```zsh
mkdir apiRefund
```
- Podemos acessar essa pasta agora, utilizando o comando `cd`:
```zsh
cd apiRefund
```
- Agora dentro da pasta do nosso projeto, podemos iniciar o nosso projeto *Node*, com o comando:
```zsh
npm init -y
```
- E podemos abrir ele no *VSCode*, com o comando:
```zsh
code .
```
- Ao abrirmos o projeto, podemos verificar e alterar as informações do arquivo `package.json`;
- E já vamos fazer a instalação das dependências que vamos utilizar, utilizando o terminal do *VSCode*:
- Instalando o `Express`:
```zsh
npm i express@4.19.2
```
- Instalando as tipagens do `Express`:
```zsh
npm i @types/express@5.0.0 -D
```
- Instalando o `TypeScript`:
```zsh
npm i typescript@5.7.3 -D
```
- Instalando o `tsx`
```zsh
npm i tsx@4.19.2 -D
```
- Instalando o `ts-node`
```zsh
npm i ts-node@10.9.2 -D
```
