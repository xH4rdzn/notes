___
- Para podermos evitar de ficar reiniciando o nosso servidor a cada mudança, podemos criar um script, para ele fazer isso de maneira automática
- Então em nosso arquivo `package.json`, vamos adicionar o script:
```json
"dev": "node --watch src/server.js"
```