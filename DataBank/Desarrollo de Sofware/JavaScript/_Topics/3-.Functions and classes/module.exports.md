Se utiliza para poder exportar a otros archivos variables, clases, funciones, entre otras cosas.

### Exportar variables o funciones
```js
function add()

let pi

module.exports = {
    add,
    pi
};
```
##### Import 
```js
const { function } = require('something');
//Or
const pi = require('something');
```

#### Exportar funciones 

###### 1. module.exports.func = new func());

Aquí, estás creando una nueva instancia de la clase funcy la estás asignando a la propiedad funce` del objeto `module.exports`. Esto significa que `_monitoringService` estará disponible para ser importado en otros módulos.

<font color="#fdeada">Este enfoque es útil cuando quieres exportar múltiples objetos, funciones o valores desde el mismo módulo. Cada uno se asigna a una propiedad diferente en el objeto `module.exports`</font>.
```js
class service(){
	async()
	async()
	async()
}

module.exports._monitoringService = new monitoring_service();
//Import
const { service }=require("path")

```
###### 2. module.exports = summary_controller; 
  
Aquí, estás reemplazando el objeto `module.exports` completo con `summary_controller`. Esto significa que cuando importas este módulo en otro lugar, obtendrás directamente `summary_controller`.

<font color="#fdeada">Este enfoque es útil cuando tienes un valor principal que quieres exportar (como una clase o una función), y no necesitas exportar nada más desde el módulo.</font>

```js
class controller {
    constructor(app){
        router.post("tu",ah );
    }
}
module.exports = controller;
//Import
const controller = require("path)
```

### Export before declarations
Esto se hace para exportar cosas directamente cuando son creadas, util por si se quiere exportar estrcuturas.
```js
// export an array
export let months = ['Jan', 'Feb', 'Mar','Apr', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];

// export a constant
export const MODULES_BECAME_STANDARD_YEAR = 2015;

// export a class
export class User {
  constructor(name) {
    this.name = name;
  }
}
```

### Export apart from declarations
```js
function sayHi(user) {
  alert(`Hello, ${user}!`);
}

function sayBye(user) {
  alert(`Bye, ${user}!`);
}

export {sayHi, sayBye};
```

### Export default
se utiliza para exportar una función, objeto o clase como el valor por defecto desde un módulo. Esto es especialmente útil cuando trabajas con múltiples módulos en un proyecto de desarrollo web, ya que facilita la organización y reutilización del código.
```js
export default class User { // just add "default"
  constructor(name) {
    this.name = name;
  }
}
///
import User from './user.js'; // not {User}, just User

new User('John');
```

### Export and Export "as"

```js
export {sayHi as hi, sayBye as bye};
///
import * as say from './say.js';

say.hi('John'); // Hello, John!
say.bye('John'); // Bye, John!
```

### Dynamic Imports
