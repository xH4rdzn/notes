___
- Hoisting (levantar ou içar) se refere ao comportamento do interpretador de *mover as declarações* de variáveis e funções para o *topo do escopo em que foram definidas*, antes mesmo da execução do código.
- Esse comportamento possibilita usar uma variável ou função antes que ela esteja definida.

### Hoisting de variáveis
- Todas as declarações de variáveis são movidas para o topo do seu escopo independentemente de onde tenha sido declarada, ela estará disponível para uso em todo o escopo em que foi definida.
- **Importante:** mesmo que as declarações de variáveis sejam movidas para o topo do escopo, elas ainda precisam ser declaradas antes de serem utilizadas. Caso contrário, você receberá uma referência indefinida (*undefined*).

### Hoisting de funções
- Todas as declarações de funções também são movidas para o topo do seu escopo. Isso significa que você pode chamar uma função antes mesmo de declará-la.
- Essa característica do Javascript permite que você organize seu código de forma mais intuitiva, definindo as funções em qualquer ordem que desejar.