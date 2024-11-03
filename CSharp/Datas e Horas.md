___
- Para criar variáveis que recebem Datas, e temos interesse apenas na data usamos o `DateOnly` e declaramos ele da seguinte maneira:
```c#
DataOnly dia = new DateOnly();
```
- Caso não passamos nada para ele vai ser gerado uma Data de acordo com o idioma da sua máquina.
- Mas para passar uma data especifica passamos na seguinte ordem: ano, mês, dia.
```c#
DateOnly dia = new DateOnly(2024, 10, 19);
```
- No Console, vai ser exibido de acordo com o idioma da sua máquina também, mas podemos alterar isso da seguinte maneira:
```c#
string diaEmTexto = dia.ToString(new CultureInfo("pt-BR"));
```
- Mas também podemos passar o formato que queremos que essa data seja exibida:
```c#
string diaEmTexto = dia.ToString("dd/MMMM/yyyy", new CultureInfo("pt-BR"));
```
- `dd` -> Dias com dois dígitos
- `MMMM` -> O nome do mês
- `yyyy` -> Ano por inteiro
#### DateTime
- É usado para Data e Horas e podemos usar da seguinte maneira:
```c#
DateTime dia1 = DateTime(2024, 10, 19, 17, 27, 30);
```
- Passamos na ordem: ano, mês, dia, hora, minutos, segundos.
- Caso quisermos pegar apenas o agora usamos o método `Now`
```c#
DateTime dia1 = DateTime.Now;
```
- O detalhe do `Now`, ele está pegando a Data e a hora da sua máquina.
- Para solucionar esse problema do `Now`, usamos o `UtcNow`