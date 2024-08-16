Pasos para crear una pagina HTTP local (Todo esto puede estar en un archivo llamado www):

###### 1-.Importar modulos
```js
const http = require("http");
const app = require("../app");
```

###### 2-.Obstener puerto:
Se obtiene el puerto desde los argumentos de la línea de comandos, las variables de entorno o se usa el puerto 3016 por defecto.
```js
const port = process.argv[2] || process.env.PORT || 3016;
```

###### 3-.Crear el servidor usando la aplicacion express
```js
const server = http.createServer(app);
```

###### 4-.Escuchar el puerto: 
El servidor comienza a escuchar en el puerto especificado y se define un manejador de errores.
```js
server.listen(port);
server.on("error", onError);
```

###### 5-.Manjeador de errores: 
Esta función maneja los errores que pueden ocurrir al intentar escuchar en el puerto, como permisos insuficientes (`EACCES`) o el puerto ya está en uso (`EADDRINUSE`).

```js
function onError(error) {
  if (error.syscall !== "listen") {
    throw error;
  }
  const bind = "Port " + port;
  switch (error.code) {
    case "EACCES":
      console.error(bind + " requires elevated privileges");
      process.exit(1);
      break;
    case "EADDRINUSE":
      console.error(bind + " is already in use");
      process.exit(1);
      break;
    default:
      throw error;
  }
}
```

###### 6-. Configurar el package.json:
Este es un paso importante por que aqui se declarara que programa se corre primero entre otras cosas a tomar en cuenta

```json
{
  "name": "name",
  "version": "1.0.0",
  "description": "description",
  "main": "./bin/www.js",
  "scripts": {
    "dev": "nodemon --max-old-space-size=4096 ./bin/www.js",
    "start": "node --max-old-space-size=4096 ./bin/www.js"
  },{}
 }
 //O tambien esto que no entiendo
"dev": "set NODE_ENV=d&& nodemon ./bin/www.js",
"start": "set NODE_ENV=p&& nodemon ./bin/www.js"
```

