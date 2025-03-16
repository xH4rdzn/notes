___
-  Como vimos tudo no javascript é uma *cadeia de prototype*, até que chegue em seu valor `null`, eles vão herdando entre os `prototypes`;
- Podemos criar objetos e verificar os seus `protypes`
```js
const adress = {
	city: "São Paulo",
	country: "Brazil",
}

// No log, podemos conferir a sua cadeia de prototypes
console.log(adress)

```