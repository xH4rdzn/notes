___
- Os modificadores de acesso, são utilizados para definir o acesso dos membros de uma classe, podem ser propriedades ou métodos, em relação a classe e o que está fora da classe. Existem 4 modificadores de acesso que são:
- `public` -> Significa que qualquer outra classe que tenha uma instancia do objeto, podem fazer o uso.
- `internal`-> Só pode ser usados em classes que estão dentro do mesmo projeto
- `private` -> Somente a classe especifica pode fazer uso.
```C#
class Carro {
	public void Teste1() {
		Console.WriteLine("Teste1");
	}

	private void Teste2() {
		Console.WriteLine("Teste2");
	}

	internal void Teste3() {
		Console.WriteLine("Teste3");
	}
}
```
- Quando não usamos modificadores de acesso em métodos por padrão eles são `private`
- Em Classes, podemos usar apenas dois modificadores de acesso o `public` e o `internal`. Se não atribuirmos nenhum modificador de acesso para a classe por padrão será atribuído o `internal`
- Existe ainda o `protected`
