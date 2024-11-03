___
- `Enums` são um grupo de opções.
- Não podemos criar um `enum` em métodos.
- Para criar um `enum`, fazemos da seguinte maneira:
```c#
enum NivelDeDificuldade {
	Baixo,
	Medio,
	Alto
}
```
- Podemos passar quantas opções quisermos
- Podemos definir valores para cada opção do `enum`
```c#
enum NivelDeDificulcade {
	Baixo = 0,
	Medio = 1,
	Alto = 2
}
```
- Caso queiramos pegar o valor que está definido para a opção precisamos fazer o que chamamos de `casting`, seguindo o exemplo abaixo:
```c#
enum NivelDeDificulcade {
	Baixo = 0,
	Medio = 1,
	Alto = 2
}

NivelDeDificuldade nivel = NivelDeDificuldade.Alto;

// Casting
int nivelEmInteiro = (int)nivel;
```