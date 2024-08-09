
#### Interacciones con iteraciones

##### In a [[while-js]] or [[do..while-js]] loop, it jumps back to the condition.
```javascript
let i = 0;
while (i < 5) {
    i++;
    if (i === 3) continue;
    console.log(i);  // Imprime 1, 2, 4, 5
}
```
##### In a [[for-js]] loop, it jumps to the update expression.
```javascript
for (let j = 0; j < 5; j++) {
    if (j === 3) continue;
    console.log(j);  // Imprime 0, 1, 2, 4
}
```
##### In a [[for...in]], [[for...of,]] or [[for await...of ]]loop, it jumps to the next iteration.
```javascript
let array = [1, 2, 3, 4, 5];
for (let value of array) {
    if (value === 3) continue;
    console.log(value);  // Imprime 1, 2, 4, 5
}
```


#### Interaccion continue y [[break-js]]

```javascript
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        continue;  // Salta la iteración cuando i es igual a 5
    }
    if (i === 8) {
        break;  // Termina el bucle cuando i es igual a 8
    }
    console.log(i);
}
// Imprime 0, 1, 2, 3, 4, 6, 7
```