___
- Dentro da pasta `src`, vamos criar uma pasta com o nome de `components`
- Dentro dessa pasta vamos colocar todos os nossos componentes, como no exemplo que vamos criar um componente de botão, então criamos o arquivo `button.tsx`e dentro dele:
```tsx
export function Button() {
	return <button>Clique Aqui</button>
}
```
- Agora para usar esse componente, precisamos importar ele e fazer a seguinte declaração:
```tsx
// Importando o componente
import { Button } from './components/button'


// Usando o componente
<Button />
```
