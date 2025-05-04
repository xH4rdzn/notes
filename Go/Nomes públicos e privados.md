___
- Para declarar uma variável, usamos a *keyword*: `var`
```go
var Foo string
```
- E uma constante segue o mesmo estilo, porém com a *keyword*: `const`
```go
const Bar string = "bar"
```
- Em `Go`, para sabermos se o nome é público ou privado, devemos olhar para a primeira letra do nome:
```go
// Variável, Função e etc público
var Foo string

// Variável, Função e etc privado
const bar string
```
- Para criar um novo pacote em `Go`, criamos uma pasta com o nome que queremos dar ao pacote e todos os arquivos devem ter o `package`
- Todos os arquivos que estão dentro de uma pasta pertencem ao mesmo pacote
- As variáveis que começam com a letra maiúscula, são exportadas automaticamente. 
- O pacote `main`não pode ser importado.
- Outra exceção são arquivos que estão dentro de uma pasta com o nome de `Internal`, apenas o pacote onde se encontra essa pasta.