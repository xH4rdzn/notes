___
- Vimos como [[Fazendo o primeiro bind mount|fazer o nosso primeiro bind mount]] da maneira mais simples possível.
- Mas também podemos fazer de uma maneira mais detalhada;
- Pois podemos usar o comando `-v`, tanto para *bind mounts* como para *volumes*, então para fazer um *bind mount* de maneira mais detalhada, usamos o comando `--mount`, que é demonstrado a seguir:
```zsh
docker run -d -p 8080:80 --mount type=bind,source=$(pwd)/my_paste,target=/usr/share/nginx/html nginx
```
- Onde o `type`é o tipo entre *Bind* e *Volume*;
- O `source`é o caminho absoluto de qual pasta vamos querer mapear para o nosso container;
- O `target` é o local para onde essa pasta vai em nosso container;