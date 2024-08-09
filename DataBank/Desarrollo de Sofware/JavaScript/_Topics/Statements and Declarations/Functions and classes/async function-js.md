 Son una parte importante de JavaScript, especialmente cuando se trata de manejar operaciones asíncronas. Aquí te dejo una introducción a las funciones asíncronas.
 ```javascript
async function miFuncion() {
  return '¡Hola, mundo!';
}
```

#### Return promise
Una función asíncrona siempre devuelve una promesa. Si el valor retornado no es una promesa, JavaScript automáticamente lo envuelve en una promesa resuelta con ese valor
```javascript
miFuncion().then(console.log);  // Salida: '¡Hola, mundo!'
```

