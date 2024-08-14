La iteración asíncrona permite iterar sobre datos que llegan de manera asíncrona, es decir, datos que no están disponibles de inmediato y pueden llegar en diferentes momentos. Los generadores asíncronos (`async generators`) facilitan aún más este proceso, permitiendo manejar flujos de datos asíncronos de manera eficiente.

Se utilizan en situaciones donde los datos se reciben de manera asíncrona, como:

- Descarga de datos en fragmentos a través de una red.
- Lectura de archivos grandes en partes.
- Procesamiento de flujos de datos en tiempo real, como eventos de usuario o datos de sensores.

### Recall Iterables
Los iterables son objetos que implementan el método `Symbol.iterator` y pueden ser iterados usando un bucle [[for-js#Bucle `for...of`]]. Aquí tienes un ejemplo básico:
```javascript
let rango = {
    from: 1,
    to: 5,
    Symbol.iterator {
        return {
            current: this.from,
            last: this.to,
            next() {
                if (this.current <= this.last) {
                    return { done: false, value: this.current++ };
                } else {
                    return { done: true };
                }
            }
        };
    }
};

for (let valor of rango) {
    console.log(valor); // 1, 2, 3, 4, 5
}
```

### Async Iterabls
Los iterables asíncronos son similares a los iterables, pero sus valores se obtienen de manera [[async_await]]. Se implementan usando `Symbol.asyncIterator` y el método `next` devuelve una [[promise()]].
```javascript
let rangoAsincrono = {
    from: 1,
    to: 5,
    Symbol.asyncIterator {
        return {
            current: this.from,
            last: this.to,
            async next() {
                await new Promise(resolve => setTimeout(resolve, 1000)); // Espera 1 segundo
                if (this.current <= this.last) {
                    return { done: false, value: this.current++ };
                } else {
                    return { done: true };
                }
            }
        };
    }
};

(async () => {
    for await (let valor of rangoAsincrono) {
        console.log(valor); // 1, 2, 3, 4, 5 (uno por segundo)
    }
})();
```

### Async Generators
Los generadores asíncronos combinan la funcionalidad de los generadores y los iterables asíncronos. Se definen usando `async function*` y permiten usar `await` dentro de ellos.

```javascript
async function* generadorAsincrono() {
    yield await Promise.resolve(1);
    yield await Promise.resolve(2);
    yield await Promise.resolve(3);
}

(async () => {
    for await (let valor of generadorAsincrono()) {
        console.log(valor); // 1, 2, 3
    }
})();
```

### Resumen

- **Iteración Asíncrona**: Permite manejar datos que llegan de manera asíncrona.
- **Iterables**: Objetos que implementan `Symbol.iterator` y pueden ser iterados con `for...of`.
- **Iterables Asíncronos**: Usan `Symbol.asyncIterator` y devuelven promesas.
- **Generadores Asíncronos**: Definidos con `async function*`, permiten usar `await` y manejar flujos de datos asíncronos de manera eficiente.