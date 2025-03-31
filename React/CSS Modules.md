___
- Podemos chamar também de CSS Escopado;
- Podemos também aproveitar para organizar os nossos componentes fazendo da seguinte maneira:
	- Criar uma pasta para o componente;
	- Criar o arquivo `index.tsx`
	- Criar o arquivo de estilização com o nome de: `styles.module.css`
- Agora para usar as estilizações desse arquivo podemos seguir como no exemplo abaixo:
```tsx
import styles from './styles.module.css'

// Usando as classes CSS
<Button className={styles.container}/>
```
- Desta maneira, podemos deixar as estilizações separadas por componentes;