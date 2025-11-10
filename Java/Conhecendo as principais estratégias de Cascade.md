___
### Entendendo a operação de cascade
- Uma operação de ***cascade*** permite propagar automaticamente operações realizadas em uma *entidade pai para suas entidades filhas* de forma automática

### Vantagens e riscos
- Vantangens -> Facilita a gestão de relacionamentos complexos ao garantir que as mudanças em uma entidade principal sejam refletidas nas entidades associadas.
- Riscos -> Se mal utilizada, pode ocasionar grandes dores de cabeça pois poderemos replicar operações de forma involuntária.

### Quais são os tipos de Cascade ?
- Existem os tipos de cascade **DETACH** E **REFRESH**, porém são raramente utilizados
- Os tipos mais usados serão vistos abaixo
### Conhecendo o tipo CascadeType.ALL
- - Replica *todas as operações* da entidade pai para entidade filha (inserção, atualização, remoção, refresh e detach)

### Conhecendo o tipo CascadeType.PERSIST
- Replica as *operações de inserção* da entidade pai para entidade filha

### Conhecendo o tipo CascadeType.MERGE
- Replica as *operações de atualização* da entidade pai para entidade filha

### Conhecendo o tipo CascadeType.REMOVE
- Replica as *operações de remoção* da entidade pai para entidade filha