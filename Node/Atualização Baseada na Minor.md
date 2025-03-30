___
- Para atualizar a versão de uma dependência que está em nosso projeto, mais atual e compatível, baseado na Minor da versão que estamos utilizando.
- Se em nosso `package.json`a depedencia tiver com um `^`, podemos instalar novamente que ele vai atualizar ela, respeitando a compatibilidade com a Minor
```json
"dependencies": {
	"express": "^3.19.0"
}
```
- Instalando novamente:
```zsh
npm i express
```
- Resultado no `package.json`:
```json
"dependencies": {
	"express": "^3.21.2"
}
```