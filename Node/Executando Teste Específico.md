___
- Para criar um arquivo de teste devemos criar seguindo a norma de nomenclatura abaixo:
```text
sum.test.ts
sum.spec.ts
```
*Nota-se que usamos as palavras `spec`ou `test`e depois passamos a extensão do arquivo.*
- Precisamos seguir essas normas de nomenclatura, para que o `Jest`, considere esse arquivo, como um arquivo de testes;
- E agora para criar um teste, usamos a função `test`do `Jest`;
```ts
test("", () => {
	console.log("teste ok!")
})
```
- *O primeiro parâmetro é o nome do teste;
- *O segundo parâmetro é uma função que vai ter o que queremos executar dentro do teste;
- Agora para executar o nosso teste podemos fazer da seguinte forma:
```zsh
npx jest caminhoParaArquivoDeTeste
```
*Como por exemplo:*
```zsh
npx jest src/sum.test.ts
```