___
- Máquinas Virtuais (VMs):
	- Cda VM executa um sistema operecional completo, incluindo kernel, e utiliza um `hypervisor` para gerenciar várias VMs no mesmo hardware. Isso resulta em maior consumo de recursos, maior tempo de inicialização e menor eficiência em termos de uso de memória e CPU.
- Containers:
	- Compartilham o kernel do sistema operacional do host, isolando apenas o aplicativo e suas dependências. Isso os torna significativamente mais leves, permitindo um uso mais eficiente de recursos e uma inicialização quase instantânea. Containers são ideais para cenários que exigem rṕida escalabilidade e alta densidade de aplicativos em um único host;