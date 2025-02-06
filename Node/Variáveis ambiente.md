___
- Variáveis ambiente, são variáveis que mudam de acordo com o ambiente em que se está;
- Podemos ter diversos ambientes como: *desenvolvimento*, *produção*, *testes* entre outros;
- Para trabalhar com as variáveis ambiente no Node, na raiz do nosso projeto precisamos criar o arquivo: `.env`;
- E precisamos da extensão `DotEnv`do VSCode;
- Precisamos instalar a biblioteca no projeto também, para isso usamos o comando:
```zsh
npm i dotenv
```
- Assim as variáveis ficam disponíveis em:
```ts
process.env.VARIAVEL
```
- Esse arquivo não entra no controle de versão, geralmente criamos um arquivo `.env-example`, colocamos quais são as variáveis que são necessárias para poder rodar a aplicação. 