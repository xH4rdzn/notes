___
- Os generics em TypeScript são utilizados para deixar a tipagem flexível, permitindo que um tipo seja definido durante a utilização de uma função ou classe. Isso possibilita a reutilização de código com diferentes tipos de dados, tornando o código mais genérico e flexível.
- Onde:
	- S -> Representa `state`ou estado;
	- T -> Representa `type`ou tipo;
	- K -> Representa `key`ou chave;
	- V -> Representa `value`;
	- E -> Representa `element`;
- E podemos fazer da seguinte maneira:
```ts
function useState<T extends string | number = string>() {
    let state: T;

    function get(){
        return state;
    }

    function set(newValue: T){
        state = newValue;
    }

    return {get, set};
}

let newState = useState<string>();
newState.get()
newState.set("Rodrigo")
newState.set(123)
newState.set("Amanda")
```