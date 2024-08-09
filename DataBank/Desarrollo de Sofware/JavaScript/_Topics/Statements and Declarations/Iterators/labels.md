 La etiqueta (label) es un identificador que puedes usar para marcar una declaración o un bloque de código. Las etiquetas se pueden usar con las declaraciones break y continue para controlar el flujo del programa de manera más precisa.
```javascript
loop1: for (let i = 0; i < 3; i++) {
    loop2: for (let j = 0; j < 3; j++) {
        if (i === 1 && j === 1) {
            continue loop1;
        }
        console.log(`i = ${i}, j = ${j}`);
    }
}
// Imprime: i = 0, j = 0; i = 0, j = 1; i = 0, j = 2; i = 1, j = 0; i = 2, j = 0; i = 2, j = 1; i = 2, j = 2
```

#### uso con [[continue-js]]]
Cuando se cumpla la condicion continuara con el otro ciclo
```javascript
let sum = 0, a = 1;
outerloop: while (sum < 12) {
    a = 1;
    innerloop: while (a < 3) {
        sum += a;
        if (a === 2 && sum < 12) {
            continue outerloop;
        }
        console.log(`sum = ${sum} a = ${a}`);
        a++;
    }
}
// Imprime: sum = 1 a = 1; sum = 4 a = 1; sum = 7 a = 1; sum = 10 a = 1; sum = 12 a = 2
```
#### uso con [[break-js]]
Cuando se cumpla la condicion rompera el otro ciclo.
```javascript
let i, j;
loop1: for (i = 0; i < 3; i++) {
    loop2: for (j = 0; j < 3; j++) {
        if (i === 1 && j === 1) {
            break loop1;
        }
        console.log(`i = ${i}, j = ${j}`);
    }
}
// Imprime: i = 0, j = 0; i = 0, j = 1; i = 0, j = 2; i = 1, j = 0
```