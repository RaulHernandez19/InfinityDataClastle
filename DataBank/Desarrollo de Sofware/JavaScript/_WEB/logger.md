La función `logger` sirve para registrar eventos o mensajes en tu aplicación. Esto es útil para depurar y entender el flujo de ejecución de tu programa.

1-.**Definición de la función logger**

Esta función toma tres argumentos: `section`, `message` y `type`. Crea una marca de tiempo (`timestamp`) y luego imprime un mensaje en la consola que incluye la marca de tiempo, el tipo de mensaje, la sección donde ocurrió y el mensaje en sí.

```js
const logger = (section, message, type) => {
  const timestamp = new Date();
  console.log(
    `${timestamp.toISOString()}: ${type} in section ${section}: ${message}`
  );
};
```

**2-.Funcion la funcion logger**

```js
module.exports = logger;
```