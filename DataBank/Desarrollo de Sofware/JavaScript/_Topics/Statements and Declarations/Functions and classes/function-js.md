Una función es un procedimiento de JavaScript: un conjunto de instrucciones que realiza una tarea o calcula un valor. Para usar una función, debes definirla en algún lugar del ámbito desde el cual deseas llamarla.
```javascript
function suma(a, b) {
  return a + b;
}

console.log(suma(1, 2));  // Salida: 3
```

### Funciones como valores
Las funciones son valores de primera clase en JavaScript, lo que significa que pueden ser utilizadas como cualquier otro valor. Por ejemplo, puedes almacenar funciones en variables, objetos y arrays; puedes pasar funciones como argumentos a otras funciones, y puedes tener funciones que retornen otras funciones.

```javascript
let misFunciones = [suma, function() { return '¡Hola, mundo!'; }];
console.log(misFunciones0);  // Salida: 3
console.log(misFunciones1);  // Salida: '¡Hola, mundo!'
```