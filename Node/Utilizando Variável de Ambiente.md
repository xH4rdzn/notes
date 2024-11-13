___
- Utilizamos variáveis de ambiente para dados sensíveis, no quais não queremos inserir dentro do código da nossa aplicação;
- Para criar uma variável ambiente, precisamos primeiro criar um arquivo para poder alocar as nossas variáveis, para criar a nossa variável de ambiente vamos seguir os passos abaixo:
1. Na raiz do nosso projeto vamos criar um arquivo com o nome de `.env`
2. Dentro desse arquivo criamos as nossas variáveis de ambiente como no exemplo abaixo:
```.env
AUTH_SECRET=igor
```
- Nota-se que usamos as `""`, apenas quando temos *espaço*;
3. Agora para ler o nosso arquivo `.env`, voltamos ao `package.json`, e no script de `dev`, alteramos para:
```json
"scripts": {
	"dev": "tsx watch --env-file=.env src/server.ts"
}
```
4. Agora temos todas as variáveis disponíveis em nossa aplicação, e para fazer seu uso, seguimos o exemplo abaixo:
```ts
return response.json({message: process.env.USER_NAME})
```
- Sempre que alterarmos as variáveis ambiente, a nossa aplicação precisa ser reiniciada;
- o arquivo `.env`, deve estar no arquivo `.gitignore`, podemos mandar um arquivo de exemplo, sem os valores das variáveis esse arquivo é o `.env-example`;
