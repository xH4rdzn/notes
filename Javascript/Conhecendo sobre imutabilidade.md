___
### Imutabilidade
- Uma vez que algo *imutável* é criado *você não pode modificar seus valores e propriedades*. Em vez disso, você cria uma cópia modificada para manter o original inalterado.
```js
// Não é uma cópia, mas sim uma referência
const address1 = {
	street: "Av. Brasil",
	number: 20,
}

// Altera a propriedade number no address1
const address2 = address1
address2.number = 30;
```

### Estratégia
- Geralmente há duas maneiras de alterar dados. A primeira é mutar o dado alterando diretamente seu valor.
- A segunda maneira é *substituir o dado antigo* por uma *nova cópia com as alterações desejadas*.
```js
const address1 = {
	street: "Av. Brasil",
	number: 20,
}

// Cópia o objeto address1, criando um novo objeto em memoria
const address2 = {...address1}
address2.number = 30
```
### Na criação de interface
- A imutabilidade é utilizada para otimizar a atualização do DOM(Document Object Model) e para fornecer um modelo mais previsível no desenvolvimento de interfaces (UI).

### Detectar Mudanças
- *Detectar mudanças e objetos mutados é difícil*, como eles são modificados diretamente a detecção do que mudou exatamente requer um objeto mutado para ser comparado com as cópias das suas próprias versões anteriores e a árvore inteira do objeto para ser cruzada.
- Detectar *mudanças em objetos imutáveis é consideravelmente fácil*. Se ele for diferente do anterior, concluímos que o objeto foi alterado.