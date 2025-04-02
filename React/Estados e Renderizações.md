___
### Render
- Antes dos seus componentes serem exibidos na tela eles devem ser renderizados pelo *React*.


### Etapa 1 - Acionar
- Há **duas razões** para um componente renderizar
1. *Quando é a renderização inicial do componente.* Quando o seu aplicativo é iniciado a renderização inicial é acionada.
2. *O estado do componente mudou.* A atualização do estado do componente enfileira automaticamente uma renderização. Você pode imaginar o cliente do restaurante pedindo mais coisas.

### Etapa 2 - Renderiza seus componentes
- Depois de acionar uma renderização o React chama seus componentes para descobrir o que exibir na tela.
- O *Rendering* é o React chamando seus componentes
- Na *renderização inicial*, o React chamará o componente raiz.
- Para *renderizações* o React chamará o componente de função cuja atualização de estado acionou a renderização
- *Esse processo é recursivo*. O componente também pode disparar um gatilho para renderizar algo em seguida, e assim por diante.
- O processo continuará até que não haja mais componentes aninhados e o React saiba exatamente o que deve ser exibido na tela.

### Etapa 3 - React confirma as alterações no DOM
- *Após renderizar (chamar) seus componentes, o React modificará o DOM*.
- Para a *renderização inicial* o React usará a API DOM para colocar todos os nós DOM criados na tela.
- Para *re-renderização* o React aplicará as operações mínimas necessárias (calculadas durante a renderização) para fazer o DOM corresponder à saída de renderização mais recente.

*O React só altera os nós DOM se houver uma diferença entre as renderizações.*
