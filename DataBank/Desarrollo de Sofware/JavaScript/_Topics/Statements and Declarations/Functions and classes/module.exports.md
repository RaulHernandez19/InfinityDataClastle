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