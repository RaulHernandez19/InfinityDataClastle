Existe sinteticamente anidado a una funcion devolviendo un valor, multiples valores, conjuntos de los mismos o None. ^f89dd0

#### <font color="#d99694">Funciones regulares</font>
```python
def suma(a, b):
    return a + b

resultado = suma(3, 4)  # resultado es 7
```

#### <font color="#d99694">En funciones dentro de un bloque try/finally</font>
Se return se encuentra dentro de esta statement se ejecutara primero el [[finally]] y despues el return

```python
def prueba():
    try:
        return 'desde try'
    finally:
        print('desde finally')

print(prueba())  # imprime 'desde finally' y luego 'desde try'
```

#### <font color="#d99694">En generadores</font>
El return dentro de un generador indica que ha terminado, lanzando asi una expeccion `stopIteration`, retornando asi el valor `StopIteration.value`
```python
def generador():
    yield 1
    yield 2
    return 3

g = generador()
print(next(g))  # imprime 1
print(next(g))  # imprime 2
try:
    print(next(g))
except StopIteration as e:
    print(e.value)  # imprime 3
```

#### <font color="#d99694">En generadores asincronos</font>
En una funcion asincrona el return vacio indica que el valor asincrono a terminado, lanzando asi un StopAsyncIteration. Minetras que si no esta vacia seria un error de sintaxis.

```python
async def generador_async():
    yield 1
    return  # Correcto

async def generador_async_erroneo():
    yield 1
    return 'algo'  # Error de sintaxis
```
