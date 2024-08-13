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

### [[callbacks]] functions
Es la forma de pasar funciones como argumentos.
```js
function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
}

function showOk() {
  alert( "You agreed." );
}

function showCancel() {
  alert( "You canceled the execution." );
}

// usage: functions showOk, showCancel are passed as arguments to ask
ask("Do you agree?", showOk, showCancel);
```

Aqui otra forma de mandar funciones cortas:
```html
<!DOCTYPE html>
<script>
"use strict";
function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
}
ask(
  "Do you agree?",
  function() { alert("You agreed."); },
  function() { alert("You canceled the execution."); }
);
</script>
```

### Function Expression vs Function Declaration
Cuando la function es una expression no cuenta con `hoisting`(La propiedad de que puede ser lamada abajo o arriba y dara igual)
```js
// Function Declaration
function sum(a, b) {
  return a + b;
}

// Function Expression
let sum = function(a, b) {
  return a + b;
};
```

```html
<!DOCTYPE html>
<script>
"use strict";
let age = prompt("What is your age?", 18);
let welcome;

if (age < 18) {
  welcome = function() {
    alert("Hello!");
  };

} else {
  welcome = function() {
    alert("Greetings!");
  };

}
welcome(); // ok now
</script>
```
