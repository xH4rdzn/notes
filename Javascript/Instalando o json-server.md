___
- O `Json Server`, permite a gente simular o comportamento de uma API;
- Para instalar o `Json Server`, vamos usar o comando abaixo:
```zsh
npm install json-server
```
- Quando ele terminar de instalar, ele vai aparecer a pasta `node_modules`, `package.json`e  o `package-lock.json`;
- Agora na raiz do nosso projeto vamos criar um arquivo com o nome `server.json` e dentro dele vamos criar um objeto vazio;
```json
{}
```
- Agora vamos no arquivo `package.json`, e vamos criar um `script`
```json
"scripts": {
	"server": "json-server server.json"
}
```
- Agora para rodar esse comando usamos no terminal o seguinte comando:
```zsh
npm run server
```
- Caso precisarmos, podemos mudar o número da porta na qual o `Json-server`, vai ser executado, para isso voltamos ao `script`que criamos e fazemos a seguinte alteração:
```json
"scripts": {
	"server": "json-server server.json --port=3333"
}
```
