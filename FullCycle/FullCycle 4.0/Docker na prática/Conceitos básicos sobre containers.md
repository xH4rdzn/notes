___
### O que são containers
- Um container é uma unidade padronizada de software que empacota o código e todas as suas dependências para que um software seja executado de forma rápida e consistente em qualquer ambiente.
### Principais características
- Imutabilidade -> Containers são construídos a partir de imagens que são essencialmente snapshots imutáveis. Isso garante que o ambiente de execução seja o mesmo em qualquer lugar que o container seja implantado.
- Isolamento de processos e recursos computacionais -> Cada container opera em um espaço de usuário isolado, com seu próprio sistema de arquivos, rede e recursos de processamento. Isso permite que múltiplos containers sejam executados simultaneamente sem interferência mútua.
- Leves - É executado como um *processo* no sistema operacional
- Utilizam os recursos do Kernel do SO - Não possui a necessidade de instalar um novo S.O
	- O container é *enganado* pensando que ele tem um SO próprio
	- A visibilidade dos processos é limitada aos processos gerados por ele
- Rápido de iniciar e de ser removido ou parado - Não há necessidade de *boot*
- Utilizam **imagens**(imutáveis) para serem executados - Algo *similar a um snapshot*
- Todos os containers rodam em *Linux*;
- Acabar com o *Na minha máquina funciona*;
