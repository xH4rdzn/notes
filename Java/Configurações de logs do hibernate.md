___
- Para podermos configurar os logs das ***querys*** que estão sendo geradas, podemos adicionar a seguinte propriedade no arquivo `application.properties`
```properties
hibernate.show_sql=True
hibernate.ddl.auto=update
```