La sintaxis de `new Promise(resolve, reject)` en JavaScript se utiliza para crear una nueva Promesa ^587cfa

```javascript
let promesa = new Promise((resolve, reject) => {
    // código aquí
});
```
- `resolve` es una función que se llama cuando la promesa se resuelve exitosamente.
- `reject` es una función que se llama cuando ocurre un error.

#### Example 1
```javascript
let promesa = new Promise((resolve, reject) => {
    let condicion = true;
    if(condicion) {
        resolve('La promesa fue resuelta exitosamente');
    } else {
        reject('Hubo un error al resolver la promesa');
    }
});

promesa.then((mensaje) => {
    console.log(mensaje); // Imprime: 'La promesa fue resuelta exitosamente'
}).catch((error) => {
    console.log(error);
});
```

#### Example 2
```javascript
async function miFuncion() {
    let promesa = new Promise((resolve, reject) => {
        setTimeout(() => resolve("Promesa resuelta!"), 1000)
    });

    let resultado = await promesa; // Espera hasta que la promesa se resuelva
    console.log(resultado); // Imprime: 'Promesa resuelta!'
}

miFuncion();
```