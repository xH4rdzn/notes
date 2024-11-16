___
- Uma coleção é a reunião de objetos de mesma natureza;
- Em computação, uma coleção é um conjunto de dados geralmente do mesmo tipo que corresponde a um contexto abstrato que pode ser representado por estruturas como: *Listas, Conjuntos, Filas, Mapas, Grafos e etc*.
##### Introdução
- Na linguagem Java toda coleção é identificada como uma `java.util.Collection`, disponibilizando assim uma interface (contrato) onde cada subclassificação de `Collection` proporciona comportamentos específicos diante dos recursos citados abaixo:

| Ação            | Método      | Descrição                                                                      |
| --------------- | ----------- | ------------------------------------------------------------------------------ |
| Adicionar       | `add`       | Possibilita a inclusão de novos elementos na coleção                           |
| Adicionar Todos | `addAll`    | Adiciona todos os elementos de uma coleção em outra coleção                    |
| Remover         | `remove`    | Remove um elemento da coleção de acordo com seu índice ou algoritmo de seleção |
| Remover Todos   | `removeAll` | Remove todos os elementos da coleção (selecionados previamente)                |
| Medir           | `size`      | Retorna a quantidade de elementos de uma coleção                               |
| Limpar          | `clear`     | Limpa a coleção removendo todos os seus elementos                              |
| Verificar       | `contains`  | Verifica a existência de um elemento atribuindo algum critério                 |
| Verificar vazio | `isEmpty`   | Verifica se a coleção está vazia (sem elementos)                               |
| Percorrer       | `iterador`  | Percore ou navega sobre todos os elementos da coleção                          |
- Dependendo da coleção alguns métodos podem mudar de nome, mas fazem a mesma função;

##### Collections Framework
- Coleções em Java é um conjunto de classes e interfaces que implementam estruturas de dados de coleção comumente reutilizáveis.


| Listas     | Conjuntos     | Filas         | Mapas     | Algoritmos    |
| ---------- | ------------- | ------------- | --------- | ------------- |
| ArrayList  | HashSet       | PriorityQueue | HashMap   | Collection    |
| Vector     | LinkedHashSet |               | HashTable | Arrays        |
| LinkedList | TreeSet       |               | TreeMap   |               |
|            |               |               |           | LinkedHashMap |
