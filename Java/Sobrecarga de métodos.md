___
- A sobrecarga de métodos, nos permite criar vários métodos com o mesmo nome, dentro da mesma classe, porém com parâmetros diferentes.
- Como no exemplo a seguir:
```java

static final int TEMPO_EXPIRACAO_PADRAO_EM_MESES = 1;

void cadastrar(final Visitante visitante) {
	this.cadastrar(visitante, TEMPO_EXPIRACAO_PADRAO_EM_MESES);
}


void cadastrar(final Visitante visitante, final int tempoExpiracaoEmMeses) {
	final int tempoExpiracaoEmDias = tempoExpiracaoEmMeses * 30;
}
```
- *Nota-se que dentro do método de cima, estamos fazendo uma chamada para o método de baixo, no qual possui um tempo padrão, que é recebido pelo método de baixo.*
- Podemos fazer isso quantas vezes precisarmos, porém precisamos nos atentar ao tipo de dado dos parâmetros, pois se forem iguais ao de outro método, vai causar um erro de compilação.