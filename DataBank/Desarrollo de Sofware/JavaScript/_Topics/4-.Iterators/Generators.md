Funciones regulares con la capacidad de devolver un solo valor o ninguno, pueden pausarse  y volverse a renaudarse, esto mediante la palabra `yield`.

Los generadores son útiles cuando necesitas:

- Crear secuencias de valores bajo demanda.
- Manejar flujos de datos asíncronos de manera más controlada.
- Implementar iteradores personalizados.
```js
function* contador() {
    let i = 0;
    while (true) {
        yield i++;
    }
}

const generador = contador();

console.log(generador.next().value); // 0
console.log(generador.next().value); // 1
console.log(generador.next().value); // 2
```

### generators are iterable
Los generadores son iterables, lo que significa que puedes usarlos en bucles [[for-js#Bucle `for...of`]] y otras construcciones que esperan iterables.

```javascript
function* generadorDeNumeros() {
    yield 1;
    yield 2;
    yield 3;
}

for (const valor of generadorDeNumeros()) {
    console.log(valor);
}
// Salida: 1, 2, 3
```

### Iterador personalizado
Los generadores son especialmente útiles para crear iterables personalizados. Aquí tienes un ejemplo de cómo podrías usar un generador para iterar sobre un rango de números
```javascript
function* rango(inicio, fin) {
    for (let i = inicio; i <= fin; i++) {
        yield i;
    }
}

const iterador = rango(1, 5);

for (const valor of iterador) {
    console.log(valor);
}
// Salida: 1, 2, 3, 4, 5
```

### Yield is a Two-Way Street
La palabra clave `yield` no solo se utiliza para devolver un valor desde el generador, sino que también puede recibir un valor desde el exterior. Esto permite una comunicación bidireccional entre el generador y el código que lo llama.
```javascript
function* generador() {
    let valor = yield 'Primera pausa';
    console.log(valor); // 'Valor recibido'
    yield 'Segunda pausa';
}

const gen = generador();
console.log(gen.next().value); // 'Primera pausa'
console.log(gen.next('Valor recibido').value); // 'Segunda pausa'
```

### generator.throw
El método [[throw]] permite inyectar un error en el generador en el punto donde se encuentra pausado. Esto es útil para manejar errores de manera controlada dentro del generador.
```javascript
function* generador() {
    try {
        yield 'Inicio';
    } catch (e) {
        console.log('Error capturado:', e);
    }
    yield 'Fin';
}

const gen = generador();
console.log(gen.next().value); // 'Inicio'
gen.throw(new Error('Algo salió mal')); // 'Error capturado: Error: Algo salió mal'
console.log(gen.next().value); // 'Fin'
```

### generator.return
El método [[return-js]] finaliza el generador de manera anticipada y opcionalmente devuelve un valor. Esto puede ser útil para realizar tareas de limpieza o para detener el generador bajo ciertas condiciones.
```javascript
function* generador() {
    yield 1;
    yield 2;
    yield 3;
}

const gen = generador();
console.log(gen.next().value); // 1
console.log(gen.return('Fin').value); // 'Fin'
console.log(gen.next().done); // true
```
