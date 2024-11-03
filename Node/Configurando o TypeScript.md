___
- Quando trabalhamos com typescript, precisamos adicionar um arquivo de configuração do typescript.
- Para poder iniciar a configuração do typescript, usamos o comando:
```bash
npx tsc --init
```
- Após rodar esse comando vai ser gerado o arquivo: `tsconfig.json`.
- Para fazer as configurações acessamos o repositório do [Node Target Mapping](https://github.com/microsoft/TypeScript/wiki/Node-Target-Mapping);
- Agora pegamos as configurações de acordo com a versão do node que estamos utilizando.
- Para verificar a versão do node, no terminal usamos o comando:
```bash
node --version
```
- Alteramos as configurações necessárias e pronto.