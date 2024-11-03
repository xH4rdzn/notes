___
- Também é uma coleção de dados.
- Os dicionários é uma coleção do tipo `chave-valor`
- A chaves precisam ser valores únicos
- Para criar uma variável do tipo dicionário, seguimos o exemplo abaixo:
```c#
Dictionary<int, string> dicionario = new Dictionary<int, string>();
```
- Adicionamos com o método `Add`:
```c#
dicionario.Add(1, "Igor");
```
- Nota-se que passamos primeiramente o valor da chave, e o segundo parâmetro passamos o valor que aquela chave vai possuir.
- Para recuperar os valores de um dicionário, usamos como um array:
```c#
string value = dicionario[1];
```
- Temos métodos em dicionários, um deles é o `ContainsKey`, que possibilita que verificamos se o dicionário existe uma chave e retorna um booleano 
```c#
bool existe = dicionario.ContainsKey(1);
```