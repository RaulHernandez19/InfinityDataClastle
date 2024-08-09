Permite declarar variables limitando su alcance al bloque, declaración, o expresión donde se está usando. A diferencia de , [[Let]] no crea propiedades en el objeto global.

```javascript
let y = 10;
if (true) {
    let y = 20;  // Aquí, y es 20
}
console.log(y);  // Aquí, y es 10
```

#### Variable global
 Una variable tiene alcance global si puede ser accedida desde cualquier parte del código. En JavaScript, las variables declaradas con var fuera de cualquier función tienen alcance global.
 ```javascript
var y = 3;  // y tiene alcance global
console.log(y);  // Imprime 3

function test() {
    console.log(y);  // Imprime 3 porque y es accesible dentro de esta función
}
test();
```