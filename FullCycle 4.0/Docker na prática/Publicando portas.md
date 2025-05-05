___
- Algumas imagens expõe portas, mas se não configuradas elas são expostas apenas dentro do container.
- Mas podemos expor uma porta do nosso computador para poder fazer acesso a porta do container. Mapear a porta do container para o nosso computador.
```zsh
docker run -p 8080:80 nginx
```
- **Passamos primeiramente a porta do nosso computador, e depois passamos a porta que queremos mapear do container**
