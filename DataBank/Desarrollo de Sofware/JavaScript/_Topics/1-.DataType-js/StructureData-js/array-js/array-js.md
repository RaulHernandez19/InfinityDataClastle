Tipo de [[_Objeto-js]] que está diseñados para almacenar colecciones de datos ordenados y tienen métodos y propiedades específicas para trabajar con esos datos. ^70ea3f

#### Sintaxis basica
```javascript
let frutas = ["manzana", "banana", "pera"];
console.log(frutas); // ["manzana", "banana", "pera"]
```

Cuando se le ingresa un dato viene automaticamente con su index, empezando en 0.
## Methods basicos

-->**Acceder a los elementos**
```js
var = frutas[0]
```

-->Agregar elementos
```js
const miArray=["David","Juan","Kevin"]
miArray.push("Carlos") //PUSH Agrega al principio
miArray.unshift("Agustin") //UNSHIFT Agrega al final
```

-->**Remover elementos**
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

### Funciones

### basicas

 1.<font color="#d99694"> includes(x):</font> Deuvelve un true o false que indica si algo fue encontrado dentro de un array. 

### Avanzadas

#### <font color="#d99694">splice()</font>
Sirve para sacar de una posicion a otra posicion diferentes elementos de un array, puede usarse para sacar elementos especificos o para hacer una eliminacion especifica.
```js
elementosCuenta.splice(posTemp,posTemp+1);
```

#### <font color="#d99694">filter()</font>
Crea un nuevo array con todos los elementos que cumplan la condición implementada por la función proporcionada.
```javascript
let numeros = [1, 2, 3, 4, 5];
let pares = numeros.filter(num => num % 2 === 0);
console.log(pares); // [2, 4]
```

#### <font color="#d99694">reduce()</font>
Aplica una función a un acumulador y a cada valor de un array (de izquierda a derecha) para reducirlo a un solo valor.
```javascript
let numeros = [1, 2, 3, 4, 5];
let encontrado = numeros.find(num => num > 3);
console.log(encontrado); // 4
```

#### <font color="#d99694">find()</font>
Devuelve el primer elemento del array que cumpla con la condición implementada por la función proporcionada.
```javascript
let numeros = [1, 2, 3, 4, 5];
let encontrado = numeros.find(num => num > 3);
console.log(encontrado); // 4
```

### Ejemplos avanzados
```javascript 
//Obtener y ordenar los nombres de las personas que tengan mas de 18 anios
let nombresMayoresDeEdad = personas
  .filter(persona => persona.edad > 18)
  .map(persona => persona.nombre)
  .sort();
```
[JavaScript Array shift() Method (w3schools.com)](https://www.w3schools.com/jsref/jsref_shift.asp)