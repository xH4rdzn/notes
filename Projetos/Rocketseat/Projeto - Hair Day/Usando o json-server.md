___
- Vamos usar o `Json-Server`, para simular uma API, para instalar vamos usar o comando:
```zsh
npm i json-server@1.0.0-alpha.21
```
- Após fazer a instalação vamos no arquivo `package.json`, vamos criar um `script`, para inicializar a nossa API;
```json
"scripts": {
	"server": "json-server --watch server.json --port 3333"
}
```
- Agora na raiz do nosso projeto vamos criar um arquivo com o nome `server.json` e dentro dele vamos fazer da seguinte maneira:
```json
{
	"schedules": []
}
```
- Agora podemos usar o comando abaixo para inicializar a nossa API
```zsh
npm run server
```