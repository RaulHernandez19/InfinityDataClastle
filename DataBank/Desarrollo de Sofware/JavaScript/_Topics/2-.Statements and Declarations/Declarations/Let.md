 Permite declarar variables limitando su alcance al bloque, declaración, o expresión donde se está usando. A diferencia de `var`, `let` no crea propiedades en el objeto global.

```javascript
let y = 10;
if (true) {
    let y = 20;  // Aquí, y es 20
}
console.log(y);  // Aquí, y es 10
```

#### Alcance de bloque

^da0ce9
Una variable tiene alcance de bloque si solo puede ser accedida dentro del bloque de código donde fue declarada. Un bloque de código es cualquier porción de código encerrada entre llaves. En JavaScript, las variables declaradas con let y const tienen alcance de bloque. ^35aa70
```javascript
{
    let x = 2;  // x solo puede ser accedida dentro de este bloque
    console.log(x);  // Imprime 2
}
console.log(x);  // Error: x no está definida
```

