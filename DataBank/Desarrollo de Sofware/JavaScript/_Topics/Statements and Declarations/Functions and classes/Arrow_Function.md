Las funciones de flecha son una forma más concisa de escribir funciones en JavaScript. No tienen su propio `this`, no tienen el objeto `arguments`, y no pueden ser usadas como constructores. Son mejores para las funciones que no necesitan tener su propio estado.
```javascript
const myFunction = (param1, param2) => {
  // Cuerpo de la función
};
```

##### Comparativa
```javascript
// Función tradicional
function sum(a, b) {
  return a + b;
}

// Función de flecha
const sum = (a, b) => a + b;
```

#### This
 En las funciones de flecha, el valor de `this` es léxico. Esto significa que `this` toma el valor del contexto circundante, no del contexto de la función. En las funciones tradicionales, `this` se refiere al objeto que invocó la función.
```javascript
// Función tradicional
let obj1 = {
  value: 'Hello',
  print: function() {
    console.log(this.value);
  }
};
obj1.print();  // Imprime "Hello"

// Función de flecha
let obj2 = {
  value: 'Hello',
  print: () => {
    console.log(this.value);
  }
};
obj2.print();  // Imprime "undefined"
```

#### Ejemplos

##### Uso con  .map
En este ejemplo, para cada `numero` en `numeros`, la función de flecha devuelve el cuadrado del `numero`, creando un nuevo array `cuadrados`.
```js
let numeros = [1, 2, 3, 4, 5];
let cuadrados = numeros.map(numero => numero * numero);
console.log(cuadrados);  // Salida: [1, 4, 9, 16, 25]

```

