___
- Para utilizar outras classes criadas em nosso projeto precisamos fazer o que chamamos de **Instancia de objeto**.
- Para fazer uma instancia de objeto fazemos seguindo o exemplo:
```C#
class Program {
	static void Main() {
		Carro meuCarro = new Carro();
	}
}
```
- Percebe-se que primeiro passamos o tipo de objeto que vamos instancia, neste exemplo vamos instancia um objeto do tipo *CARRO*.
- Depois damos um nome para uma variável, em outras palavras, um local para guardar informações daquele objeto em especifico, neste exemplo demos o nome de *meuCarro*
- Usamos o `=` para atribuir um valor para a variável.
- E agora usamos a palavra `new`, para pode criar um novo objeto. Nota-se que após a keyword `new`, passamos o nome da classe que queremos instanciar, neste caso é a classe *Carro*, então usamos: `new Carro();`
- Agora para poder fazer o uso dessas funções, chamamos a variável que instanciamos e usamos um `.`, para poder chamar as funções daquele objeto
```C#
meuCarro.Ligar();
```
___
- Quando temos uma classe dentro de uma pasta e queremos fazer o uso daquela classe precisamos importar a classe que queremos usar, para fazer a importação usamos a keyword `using`
```C#
using HelloWorld.Exemplo;
```
- Desta maneira já podemos usar qualquer arquivo/classe que está no *namespace* que importamos