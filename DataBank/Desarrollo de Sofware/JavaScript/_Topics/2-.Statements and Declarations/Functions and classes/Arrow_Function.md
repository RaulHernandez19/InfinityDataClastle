Las funciones de flecha son una forma más concisa de escribir funciones en JavaScript. No tienen su propio `this`, no tienen el objeto `arguments`, y no pueden ser usadas como constructores. Son mejores para las funciones que no necesitan tener su propio estado.

>Nota: Importante recordar el hoisting, osea que no importa si la ufncion esta arriba o abajo, siempre es llamable. Y que la [[anonymousFunction]] no es hoisting, lo que es una arrow function

let variable = `valor(es) que tomara y...` <font color="#c0504d">=</font>apunta a un proceso que se le hara a valor(es)<font color="#c0504d">></font>

Funcion normal
```javascript
function saludar(nombre){
	return 'hola' + nombre;
}

console.log(saludar('David'));
```

```javascript
let saludo2=nombre=>'Saludos ' + nombre

let suma = (a,b) => {a+b};
```

- Si la funcion tiene solo un parametro se puede omitir los parentesis y si solo es una linea puede estar isn parentesis.
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

#### [[Arrow_Function]] + [[conditionalOperatorQuestion]]
Lo que esta haciendo ese codigo es que dependiendo de la edad, la funcion welcome hara uno de los dos alert.
```js
let age = prompt("What is your age?", 18);

let welcome = (age < 18) ?
  () => alert('Hello!') :
  () => alert("Greetings!");
welcome();
```

#### <font color="#d99694">Multiline arrow functions</font>
Es cierto....ES MUY CIERTO, la funcion flecha al final del dia es una forma mas simple de decir que para poder asignar cierta variable a algo debe ocurrir un proceso, asi que ese es uno de sus usos.
```js
let sum = (a, b) => {  // the curly brace opens a multiline function
  let result = a + b;
  return result; // if we use curly braces, then we need an explicit "return"
};

alert( sum(1, 2) ); // 3
```

#### Ejemplos

```js
let double = n => n * 2; //double es igual a n, que hara un proceso.
```
##### Uso con  .map
En este ejemplo, para cada `numero` en `numeros`, la función de flecha devuelve el cuadrado del `numero`, creando un nuevo array `cuadrados`.
```js
let numeros = [1, 2, 3, 4, 5];
let cuadrados = numeros.map(numero => numero * numero); //A cada elemento de numero se le aplicara numero * numero
console.log(cuadrados);  // Salida: [1, 4, 9, 16, 25]
```


```js
var colores=['rojo','azul','verde']

/*colores.foreach(function(color){
	console.log(color)
});
*/
colores.forEach((color)=>{
	console.log(color)
})
```
##### ![[for-js#Metodo `forEach`]]
aqui lo que sucede es que a cada elemento del array tendra ese proceso, tambien podria devolver algo.

