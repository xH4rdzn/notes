___
- Podemos também usar o próprio SQL, com o método `RAW`, para fazer isso fazemos da seguinte maneira:
```ts
await knex.raw("INSERT INTO courses (name) VALUES (?)", [name])
```
- Esse código faz o mesmo código que o  [[Método de Insert]] do `knex`;
- Podemos usar esse método `raw`, para os outros comandos SQL também;