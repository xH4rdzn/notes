___
- Precisamos converter o nosso código que está em *typescript* para código *javascript*, para isso vamos usar o `tsup`, que vamos instalar usando o comando:
```zsh
npm i tsup -D
```
- No arquivo `package.json`, vamos criar um script com o nome de `build`:
```json
"build": "tsup src --out-dir build"
```
- Agora rodamos esse script com o comando:
```zsh
npm run build
```
- Assim irá converter o nosso código.
- Subimos esse código para o github