___
- Os tipos de dados números do *Kotlin* são:
```kotlin
// Numéricos

val byte: Byte = -128
val short: Short = 32_500
val int: Int = 30_000
val long: Long = 60_000

val float: Float = 3.14f
val double: Double = 3.14

// Literais
val char: Char = 'a'
val string: String = "palavra"
```
- Para podermos passar os valores de uma variável dentro de uma string podemos fazer da seguinte maneira:
```kotlin
val char: Char = 'a'
val string: String = "$char $byte"
```
- E também temos o tipo `boolean`
```kotlin
val boolean: Boolean = false
```