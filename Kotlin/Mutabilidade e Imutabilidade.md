___
- Para definirmos variáveis que tem seu valor constante em *Kotlin*, usamos a keyword `val`, como no exemplo abaixo:
```kotlin
val name = "Igor Coelho"
```
- E para definirmos variáveis que podem ter seu valor alterado, usamos a keyword `var`, como no exemplo abaixo:
```kotlin
var age = 29
```
- Como já demos um valor inteiro para a variável `age`, não podemos atribuir outro tipo de dado para ela, como no exemplo abaixo:
```kotlin
var age = 29

// Vai dar erro
age = "Igor"
```
