La funcion while de toda la vida.

```js
let i = 0;
while (i < 3) { // shows 0, then 1, then 2
  console.log( i );
  i++;
}
```

### Do...while
Pues de que primero se hace algo y despues lo otro, nada nuevo.
```js
let i = 0;
do {
  alert( i );
  i++;
} while (i < 3);
```

### Interaccion con [[continue-js]]
![[continue-js#In a while-js loop, it jumps back to the condition.]]

>Nota: recordar que tambien se puede [[break-js]] y tiene un uso con [[labels]]