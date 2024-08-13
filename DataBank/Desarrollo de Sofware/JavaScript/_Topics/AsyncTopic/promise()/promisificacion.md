Las funciones basadas en callbacks pueden ser difíciles de leer y mantener, especialmente cuando se anidan múltiples callbacks, lo que se conoce como “callback hell”. Las promesas, por otro lado, permiten un manejo más limpio y estructurado del código asíncrono. ^2cdedc

Funcion que carga un script antes:
```javascript
function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;
  script.onload = () => callback(null, script);
  script.onerror = () => callback(new Error(`Error al cargar el script ${src}`));
  document.head.append(script);
}

// Uso:
loadScript('path/script.js', (err, script) => {
  if (err) {
    console.error(err);
  } else {
    console.log('Script cargado:', script);
  }
});
```
Podemos promisificar esta función para que devuelva una promesa en lugar de usar un callback:
```javascript
function loadScriptPromise(src) {
  return new Promise((resolve, reject) => {
    loadScript(src, (err, script) => {
      if (err) {
        reject(err);
      } else {
        resolve(script);
      }
    });
  });
}

// Uso:
loadScriptPromise('path/script.js')
  .then(script => console.log('Script cargado:', script))
  .catch(err => console.error(err));
```
