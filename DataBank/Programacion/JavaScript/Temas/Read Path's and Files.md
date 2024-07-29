
# Read Path's

```js
const fs = require("fs");

fs.readdir(path, (err, files) => {
    if (err) {
      console.error(err);
    } else {
      console.log(files);
    }
  });
};
```

La función `fs.readdir()` es asíncrona y utiliza un callback para manejar los resultados. Cuando llamas a `return files;` dentro del callback, no estás devolviendo los archivos desde `getAllOfDevices()`, sino desde el callback, lo que no afecta el resultado de `getAllOfDevices()`.

Para solucionar este problema, puedes envolver `fs.readdir()` en una [[Promise]] y resolverla con los archivos cuando estén disponibles.



Para leerlo independientemente de la computadora se puede usar **path.join** 

```js
const path = require("path");
const directoryPath = path.join(__dirname, path)
```

>Importante saber que se usara \\\\ para leer archivos dentro de networks

# Rutas de interes:
https://youtu.be/V806HEmJ__Y?si=FonbdgaAImRz8bNl
[Node.js File System Module (w3schools.com)](https://www.w3schools.com/nodejs/ref_fs.asp)

