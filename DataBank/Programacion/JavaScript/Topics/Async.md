Una operación asíncrona en JavaScript es una técnica que permite a tu programa iniciar una tarea de larga duración y seguir respondiendo a otros eventos mientras esa tarea se ejecuta, en lugar de tener que esperar hasta que esa tarea haya terminado

Por ejemplo, un programa puede enviar una solicitud a un servidor mientras gestiona y procesa la información del usuario, todo al mismo tiempo. De esta forma, un programa puede ejecutarse de forma mucho más eficiente

```javascript
fetch('https://api.github.com/users/github')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error(error));
```
>En este ejemplo, `fetch()` inicia una solicitud HTTP para obtener datos del usuario “github” de la API de GitHub. Esta es una operación que puede llevar algún tiempo. Sin embargo, en lugar de bloquear el resto del código y esperar a que se complete la solicitud, `fetch()` devuelve inmediatamente una `Promise`. Esta promesa se resuelve con la respuesta de la solicitud una vez que esté disponible. Mientras tanto, el resto del código puede continuar ejecutándose.


