___
- Serve como um *linter*, para o nosso código, em outras palavras serve para deixar o código padronizado;
- Primeiramente precisamos instalar ele, usando o comando abaixo:
```zsh
npm i eslint -D
```
- E junto já vamos instalar um pacote junto, usando o comando abaixo
```zsh
npm i @rocketseat/eslint-config -D
```
- Com o as bibliotecas instaladas, na raiz do nosso projeto, vamos criar um arquivo com o nome de: `.eslintrc.json`, dentro desse arquivo vamos por as configurações;
```json
{
	"extends": [
		"@rocketseat/eslint-config/node"
	]
}
```
- Precisamos também instalar a extensão do **ESLint**, para funcionar corretamente;
- E também precisamos alterar as configurações do nosso **VSCode** para:
```json
"editor.codeActionsOnSave": {
	"source.fixAll.eslint": true,
}
```
- Desta maneira, ao salvar os arquivos ele deve fazer a formatação do código;
- Para automatizar esse processo, podemos criar um *script*, para facilitar quando tiver muitos arquivos
```json
"lint": "eslint src --ext .ts --fix"
```
