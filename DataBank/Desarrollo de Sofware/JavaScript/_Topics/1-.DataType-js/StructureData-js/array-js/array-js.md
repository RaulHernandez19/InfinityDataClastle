Tipo de [[_Objeto-js]] que está diseñados para almacenar colecciones de datos ordenados y tienen métodos y propiedades específicas para trabajar con esos datos. ^70ea3f

#### Sintaxis basica
```javascript
let frutas = ["manzana", "banana", "pera"];
console.log(frutas); // ["manzana", "banana", "pera"]
```

Cuando se le ingresa un dato viene automaticamente con su index, empezando en 0.

## Methods

#### Acceder a los elementos
```js
var = frutas[0]
```

### Agregar elementos
```js
const miArray=["David","Juan","Kevin"]
miArray.push("Carlos") //PUSH Agrega al principio
miArray.unshift("Agustin") //UNSHIFT Agrega al final
```

### Remover elementos
```js
let final=miArray.pop(); //POP sacar el ultimo elemento del array
let start=miArray.shift()// SHIFT saca el primer elemento del array
```

### Iterar 

#### [[for-js]]
```js
const nombres=["PokeHugo","Pepe","Tuntun"];
for (let i=0;i<nombres.lenght;i++){
	console.log(nombres[i]);
}
```
##### ForEach
```js
nombres.forEach((elemento)=>{
	console.log(elemento)
});
```

Importante conocer: [[Object+Array]]

