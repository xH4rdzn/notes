___
- Em vez de ficarmos rodando o comando:
```zsh
npm test
```
- Podemos criar um script que roda os testes assim que fazemos uma alteração;
- Para isso precisamos ir no arquivo `package.json`, e criar um script, da seguinte maneira:
```json
{
	"test:dev": "jest --watchAll"
}
```
- Assim o `Jest` fica observando cada alteração em um arquivo de teste, e assim que tiver ele executa os testes novamente.