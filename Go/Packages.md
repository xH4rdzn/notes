___
- Os `packages`são peças fundamentais de `Go`, todo arquivo go precisa de uma declaração de pacote na primeira linha, a unica exceção são comentários.
- Podemos importar pacotes
```go
import (
	"fmt"
)
```
- E para usarmos esses pacotes devemos usar da seguinte maneira:
```go
package main

import (
	"fmt"
)

func main() {
	fmt.Println("Hello Go")
}
```
- *Nota-se que usamos `fmt`e depois a função que queremos usar, mas isso se aplica a variáveis também.*
- Podemos renomear um pacote, como no exemplo abaixo:
```go
package main

import (
	meuPacote "encoding/json"
	"fmt"
)

func main() {
	fmt.Println("Hello Go")
}
```
- E para fazer o uso desse pacote, o chamamos pelo nome que damos ao renomear, como demostrado no exemplo abaixo:
```go
package main

import (
	meuPacote "encoding/json"
	"fmt"
)

func main() {
	fmt.Println("Hello Go")

	meuPacote.Marshal()
}
```
- *Normalmente se usa isso quando estamos usando pacotes de terceiros, em pacotes `standlibs`não renomeamos. Ou se eles tiverem o mesmo nome, ai precisamos renomear.*
- Não é recomendado, mas podemos fazer o uso de `dots imports`, que puxa o pacote para o nosso pacote
```go
package main

import (
	. "fmt"
)

func main() {
	// Desta maneira não precisamos chamar por fmt
	Println("Hello Go")
}
```
