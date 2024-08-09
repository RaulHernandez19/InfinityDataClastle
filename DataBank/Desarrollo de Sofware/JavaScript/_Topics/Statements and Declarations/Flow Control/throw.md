Similar al [[assert]] de python, ofrece la posibilidad de errores personalizados.

```js
function isNumeric(x) {
  return ["number", "bigint"].includes(typeof x);
}

function sum(...values) {
  if (!values.every(isNumeric)) {
    throw new TypeError("Can only add numbers");
  }
  return values.reduce((a, b) => a + b);
}

console.log(sum(1, 2, 3)); // 6
try {
  sum("1", "2");
} catch (e) {
  console.error(e); // TypeError: Can only add numbers
}
```

```js
function getRectArea(width, height) {
  if (isNaN(width) || isNaN(height)) {
    throw new Error('Parameter is not a number!');
  }
}

try {
  getRectArea(3, 'A');
} catch (e) {
  console.error(e);
  // Expected output: Error: Parameter is not a number!
}
```