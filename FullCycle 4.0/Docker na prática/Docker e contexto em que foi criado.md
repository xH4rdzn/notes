___
- ### História do Docker

**Origem**: O Docker foi criado em 2013 por uma empresa chamada dotCloud, que oferecia serviços de Plataforma como Serviço (PaaS). Inicialmente, o Docker foi desenvolvido para uso interno, visando facilitar a implantação de aplicações.
 **Open Source**: Reconhecendo o potencial da tecnologia, a dotCloud tornou o Docker Engine open source, permitindo que a comunidade contribuísse e expandisse suas capacidades.
 **Evolução para Docker Inc.**: Com a crescente popularidade do Docker, a dotCloud mudou seu foco principal para o desenvolvimento e suporte da tecnologia Docker, renomeando-se para Docker Inc.

- Criado em 2013 por empresa chamada *dotCloud* (PaaS) para uso interno
- Docker Engine passou a ser Open Source
- Com a popularização da ferramenta, a *dotCloud* foi renomeada para Docker Inc.
- Docker Community Edition / Engine é diferente do Docker Desktop (produto da Docker Inc.)
- Docker utiliza os recusos do Linux e outros componentes
	- Ferramenta 360: gerenciamento de containers, rede e disco, além da criação e build de imagens
	- Trabalha no formato cliente-servidor
		- `Daemon` que faz o gerenciamento de todos os containers
		- Client que faz chamadas para o `daemon`
		- `Daemon` acaba se tornando um ponto único de falha (SPoF)
			- Root vs rootless