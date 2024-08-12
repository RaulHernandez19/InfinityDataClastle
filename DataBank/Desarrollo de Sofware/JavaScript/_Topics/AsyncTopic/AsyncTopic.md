La programación asíncrona permite que un programa realice múltiples tareas al mismo tiempo sin bloquear la ejecución del código. Dandoles usos como:

- **Solicitudes HTTP**: Realizar peticiones a servidores para obtener o enviar datos sin bloquear la interfaz de usuario.
- **Temporizadores**: Ejecutar funciones después de un cierto período de tiempo usando `setTimeout` o `setInterval`.
- **Operaciones de Entrada/Salida**: Leer o escribir archivos, acceder a bases de datos, etc., sin bloquear el flujo principal del programa.
## <font color="#fdeada">Tecnicas</font>

### [[callbacks]]
Una función callback es una función que se pasa como argumento a otra función y se ejecuta después de que se completa una operación asíncrona.

### [[promise()]]
![[promise()#^37359d]]

### [[async_await]]
`async` y `await` son palabras clave que simplifican el trabajo con promesas, permitiendo escribir código asíncrono de manera más legible.

| Característica        | Callbacks                                     | Promises                                                      | Async/Await                                  |
| --------------------- | --------------------------------------------- | ------------------------------------------------------------- | -------------------------------------------- |
| **Definición**        | Función pasada como argumento a otra función  | Objeto que representa el resultado de una operación asíncrona | Sintaxis que simplifica el uso de Promises   |
| **Sintaxis**          | Función dentro de otra función                | `.then()` y `.catch()`                                        | `async` y `await`                            |
| **Legibilidad**       | Menos legible, puede llevar a “callback hell” | Más legible que callbacks                                     | Muy legible, similar a código síncrono       |
| **Manejo de Errores** | A través de funciones callback adicionales    | `.catch()`                                                    | `try` y `catch`                              |
| **Uso Común**         | Operaciones simples y rápidas                 | Operaciones más complejas y encadenadas                       | Operaciones complejas con múltiples promesas |
| **Ventajas**          | Sencillo para tareas pequeñas                 | Mejor manejo de errores y encadenamiento                      | Código más limpio y fácil de entender        |
| **Desventajas**       | Difícil de mantener y depurar                 | Puede ser verboso con muchas promesas                         | Requiere soporte de ES8 (ECMAScript 2017)    |
**<font color="#fdeada">Callbacks</font>**: Útiles para tareas simples y rápidas donde la complejidad es baja.

**<font color="#fdeada">Promises</font>**: Ideales para operaciones más complejas que requieren encadenamiento y mejor manejo de errores.

**<font color="#fdeada">Async/Await</font>**: Perfectos para escribir código asíncrono de manera más limpia y legible, especialmente cuando se manejan múltiples promesas.


[Promise() constructor - JavaScript | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/Promise)