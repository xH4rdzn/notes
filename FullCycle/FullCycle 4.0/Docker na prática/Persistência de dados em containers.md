___
- Toda vez que criamos um novo *container* acontece algumas coisas, como a imagem é baixada, essa imagem foi baixada e feita em várias camadas.
- Chamamos isso de ***Overley FileSystem***, ele consegue se complementar através de camadas.
- Mas quando o nosso container entra em execução ele se separa em duas partes:
- A camada de **imagem**, que é imutável, isso significa que o container que foi gerado usou tudo daquela imagem para poder ser usado.
- A camada de **container** é a camada que temos permissões de leitura e escrita.
- Mas tudo que é escrito na camada de **container** é perdido no momento em que o container é removido.
- Mas para contornar isso temos duas opções como ***Bind Mounts*** e ***Volumes**.
