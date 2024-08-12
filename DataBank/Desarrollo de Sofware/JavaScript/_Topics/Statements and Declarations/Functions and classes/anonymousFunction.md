Son funciones que se declaran sin un nombre específico. Estas funciones son útiles cuando se desea declarar una función para su uso inmediato, y no necesariamente se necesita referenciarla más adelante.
```javascript
let variable = function(arg1, arg2, ..., argN) {
    // Código de la función
}
```

Las funciones anónimas se utilizan comúnmente como argumentos de otras funciones, especialmente cuando se utilizan funciones de orden superior que toman otras funciones como argumentos. También son útiles en patrones de programación funcional y en la programación de eventos en JavaScript.

##### Diferencias con la [[Arrow_Function]]
La funcion anonima no tiene su propio this, mientras que la flecha si.
```javascript
// Función anónima
let saludoAnonimo = function(nombre) {
    return "Hola, " + nombre;
}

// Función de flecha
let saludoFlecha = (nombre) => "Hola, " + nombre;

console.log(saludoAnonimo("Mundo")); // Imprime: "Hola, Mundo"
console.log(saludoFlecha("Mundo")); // Imprime: "Hola, Mundo"
```

##### Ejemplo practico
```javascript
let numeros = [1, 2, 3, 4, 5];

numeros.map(function(numero) {
    return numero * 2;
}); // Devuelve [2, 4, 6, 8, 10]
```