___
Iremos consumir uma API para busca de dados de séries. Para tal, criaremos a classe chamada ConsumoAPI, dentro de um pacote chamado service. Nele teremos um método chamado ObterDados, que devolve uma String com o json que corresponde à resposta da requisição.

```java
public String obterDados(String endereco) {
    HttpClient client = HttpClient.newHttpClient();
    HttpRequest request = HttpRequest.newBuilder()
            .uri(URI.create(endereco))
            .build();
    HttpResponse<String> response = null;
    try {
        response = client
                .send(request, HttpResponse.BodyHandlers.ofString());
    } catch (IOException e) {
        throw new RuntimeException(e);
    } catch (InterruptedException e) {
        throw new RuntimeException(e);
    }

    String json = response.body();
    return json;
}
```