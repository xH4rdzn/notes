___
- Podemos dividir os tipos numéricos em dois grupos o grupo dos números ***inteiros*** e o o grupo dos números é o que chamamos de ***ponto flutuante***.
- Para declarar uma variável que vai receber ou possui um valor inteiro fazemos da seguinte maneira:
```C#
int numero = 7;
```
- Existe outro tipo de inteiro que é o ***long***:
```C#
long numero2 = 7;
```
- Podemos também declarar números unsigned, em outras palavras, números sem sinal:
```C#
uint numero3 = 7;
```
- Ainda possuímos outros tipos para o grupo dos números inteiros, e o que muda entre eles são os intervalos que eles suportam. Vamos ver abaixo:
	- `sbyte` -> de -128 a 127
	- `byte` -> de 0 a 255
	- `short` -> de -32.768 a 32.767
	- `ushort` -> de 0 a 65.535
	- `int` -> de -2.147.483.648 a 2.147.483.647
	- `uint` -> de 0 a 4.294.967.295
	- `long` -> de -9,223,372,036,854,775,808 a 9,223,372,036,854,775,807
	- `ulong` -> de 0 a 18.446.744.073.709.551.615
	- `nint` -> Depende da plataforma
	- `nuint` -> Depende da plataforma
- Para facilitar a leitura de números inteiros muito grande podemos usar `_` para fazer a separação:
```c#
int numero1 = 100_000_000;
```
- Para declarar números de ponto flutuante temos 3 tipos, o `double`, `float`, `decimal`; E para declarar eles usamos o `.` e não `,`; Como no exemplo abaixo:
```C#
double numero1 = 3.14;
```
- Os tipos `float` e `decimal`, precisam de sufixos para poder ser o tipo escolhido. E usamos:
- Para `float` ->
```c#
float numero2 = 3.14f;
```
- Para `decimal` ->
```c#
decimal numero3 = 3.14m;
```
- A diferença entre eles é a precisão.
	- `float` -> 6 a 9 dígitos
	- `double` -> 15 a 17 dígitos
	- `decimal` -> 28 a 29 dígitos