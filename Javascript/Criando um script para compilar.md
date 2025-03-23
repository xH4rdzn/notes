___
- Vamos criar um `script`personalizado para poder executar o *Babel*, para isso vamos no arquivo `package.json`, e adicionamos o seguinte:
```json
"scripts": {
	"build": "babel main.js --out-dir ./dist"
}
```
- Agora para executar esse `script`, usamos da seguinte maneira:
```zsh
npm run build
```
