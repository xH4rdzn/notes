___
### Classes x Prototype
- Javascript é dinâmico e não dispõe de uma implementação de uma `class`(a palavra-chave `class` foi introduzida no ES2015, mas é *syntax sugar*, **O Javascript permanece baseado em prototype**).

### Prototype
- Quando se trata de herança, o JavaScript tem somente um construtor: objetos. *Cada objeto tem um link interno para um outro objeto chamado prototype*.
- O objeto *prototype também tem um atributo prototype*, e assim por diante *até que seu valor `null`seja encontrado como sendo o seu prototype.* O `null`que, por definição, não tem prototype, e age como um link final nesta cadeia de protótipos (**prototype chain**).
