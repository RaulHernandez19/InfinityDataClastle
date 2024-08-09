Objeto que representa la finalización eventual (o fracaso) de una operación [[Async]] y su valor resultante.

Una `Promise` es un proxy para un valor no necesariamente conocido cuando se crea la promesa. Te permite asociar manejadores con el valor de éxito eventual de una acción asíncrona o la razón del fracaso. Esto permite que los métodos asíncronos devuelvan valores como los métodos síncronos: en lugar de devolver inmediatamente el valor final, el método asíncrono devuelve una promesa para suministrar el valor en algún punto en el futuro

```javascript
let miPromesa = new Promise((resolve, reject) => {
    let x = 0;
    // El código productor (esto puede tomar algún tiempo)
    if (x == 0) {
        resolve("OK");
    } else {
        reject("Error");
    }
});

miPromesa.then(
    function(value) { console.log(value); }, // código si es exitoso
    function(error) { console.log(error); }  // código si hay algún error
);
```

