El bulce es una estructura de control que permite repetir un bloque de codigo varias veces.
```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

## <font color="#fdeada">Tipos</font>
### Bucle `for...in`
Se utiliza para iterar sobre las propiedades enumerables de un [[_Objeto-js]]
```javascript
let objeto = {a: 1, b: 2, c: 3};

for (let clave in objeto) {
  console.log(clave, objeto[clave]);
}
// Salida: a 1, b 2, c 3
```

### Bucle `for...of`

^daa6b6

Se usa para iterar sobre elementos de objetos iterables como [[array-js]], [[map-js]], etc.
```javascript
let array = [10, 20, 30];

for (let valor of array) {
  console.log(valor);
}
// Salida: 10, 20, 30
```

### Metodo `forEach`
Metodo especifico para el array que permite ejecutar una [[function-js]] para cada elemento del array.
```javascript
let array = [1, 2, 3];

array.forEach((elemento, indice) => {
  console.log(`Índice: ${indice}, Valor: ${elemento}`);
});
// Salida: Índice: 0, Valor: 1
//         Índice: 1, Valor: 2
//         Índice: 2, Valor: 3
```

## Map con For
```javascript
let mapa = new Map();
mapa.set('a', 1);
mapa.set('b', 2);

for (let [clave, valor] of mapa) {
  console.log(clave, valor);
}
// Salida: a 1, b 2
```
## Set con For
```javascript
let conjunto = new Set([1, 2, 3]);

for (let valor of conjunto) {
  console.log(valor);
}
// Salida: 1, 2, 3
```

## Interaccion con [[continue-js]]
![[continue-js#^2cb0ad]]

>Nota: recordar que tambien se puede [[break-js]] y tiene uso especifico con [[labels]]