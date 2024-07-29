Estructura de una API

# <font color="#8db3e2">Controller</font>
Aqui se encarga de configurar los llamados de la APi() se le puede incluir [[Swagger]] para documentar).

```js
const express = require('express');

class RouterController {
    constructor(app) {
    const router = new express.Router();
    try{
    router.get('/pathRouter',RouterService.gerRouter)
    app.use('',router) //Aqui dentro podria ir un prefijo de la ruta
    }catch(error){
        console.log(error);
    }
    }
}
module.exports = routerController;
```

# <font color="#8db3e2">Service</font>
Esta seccion se encarga de obtener la respuesta a mandar junto con mensajes de error o de completado. Se utiliza [[logger]]

```js
const logger = require("../../utils/logger");

class RouterService {
    async getConfig(req, res) {
      try {
        const something = await ObtainMondo.geyRouter();
        return res.send(something);
      } catch (error) {
        logger("Error getting routere", error, "Error");
        return res.status(500).send({ error: error.message });
      }
    }
  }
  module.exports = new RouterService();
```
# <font color="#8db3e2">Obtain</font>
Si se requiere se puede tener una seccion aparte o las necesarias para procesar la informacion que se obtendra de la API, ya sea por una ruta o base de datos.

```js
// Obtain the something that you need
class RouterObtain {
     getSomething = async () => {
        try {
            //Logic     
            return something;
        } catch (e) {
            throw Error(`Error: ${e}`);
        }
    }
}
module.exports = new RouterObtain();
```

# <font color="#d99694">router.module</font>

Aqui se hara un module que englobara a todos nuestros endpoints.

```js
class RouterModule { 
  constructor(app) {
    this.app = app;
  }
 init() {
    // Import Routers
    const RouterController = require('pathToRouter');

    //Init Routers
    new routerController(this.app)
  }
}
module.exports = RouterModule;
```

# HTTP API

Teniendo un [[HTTP_Js]] creado

###### 1-.Importar los modulos:
```js
const createError = require("http-errors"); // Crea errores HTTP para Express
const express = require("express"); // Framework de Node.js para crear servidores web
const logger = require("morgan"); // Registra solicitudes en la consola
const cors = require("cors"); // Habilita CORS
const bodyParser = require('body-parser'); // Analiza el cuerpo de las solicitudes
```
###### 2-.Inicializar la aplicacion Express:
```js
const app = express();
```
###### 3-.Configurar middlewares: 
Se configuran los middlewares para analizar el cuerpo de las solicitudes, registrar las solicitudes y permitir CORS.
```js
app.use(bodyParser.json());
app.use(express.json()); // Analiza el cuerpo de las solicitudes
app.use(logger("dev")); // Registra las solicitudes en la consola
app.use(cors()); // Permite solicitudes de origen cruzado (CORS)
```
###### 4-.Servir archivos estaticos: 
Se configura la aplicación para servir archivos estáticos desde el directorio public.
```js
app.use('/', express.static(__dirname + '/public'));
```
###### 5-.Inicializar rutas:
```js
async function init(app) {
    const appRouting = require("./routers/router.module");
    const appModules = new appRouting(app);
    console.log("appModules connecting routers");
    appModules.init();
}
init(app);
```

###### 6-.Manejo de errores:
```js
app.use(function (req, res, next) {
    next(createError(404));
});
```

###### 7-.Manejo de errores grandes
```js
app.use(function (err, req, res, next) {
    res.status(err.status || 500).send({ error: res.locals.message });
});
```
###### 8-.exportar la aplicacion
```js
module.exports = app;
```