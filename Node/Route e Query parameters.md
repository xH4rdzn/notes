___
- Os ***Query Parameters***, possuem uma chave e um valor, são indicados pelo símbolo `?`e podem ser concatenados com `&`, como no exemplo abaixo:
```URL
http://localhost:3333/users?userId=1&name=Igor
```
- Os *URL* com ***Query Parameters*** são Stateful, em outras palavras as informações não ficam salvas.
- Usamos para enviar dados que não são sensíveis.
- São muito utilizados para: filtros, paginação
- Eles não são obrigatórios.

#### Route Parameters
- Os ***Routes Parameters***, normalmente são utilizados para identificação de recurso
- Eles são obrigatórios
- E não podem ser usados para envio de informações sensíveis.
```url
http://localhost:3333/users/1
```


#### Request Body
- Normalmente são usados para envio de informações de um formulário
- Não aparecem na *URL*, e esses dados são criptografados. 