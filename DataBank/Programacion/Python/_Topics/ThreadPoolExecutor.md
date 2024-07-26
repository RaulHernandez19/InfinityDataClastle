Importacion: `from concurrent.futures import ThreadPoolExecutor.`

`ThreadPoolExecutor` es una clase en el módulo `concurrent.futures` de Python que permite la ejecución de operaciones en paralelo utilizando hilos. Aquí te explico sus métodos más comunes:

# Submit

(func, *args, **kwargs)**: Este método agenda la función `func` para ser ejecutada y retorna un objeto `Future`. Aquí tienes un ejemplo:

```python
from concurrent.futures import ThreadPoolExecutor

def tarea(n):
    return n * 2

with ThreadPoolExecutor() as executor:
    futuro = executor.submit(tarea, 5)
    print(futuro.result())  # Imprime: 10
```

# Map

**map(func, *iterables, timeout=None, chunksize=1)**: Este método es similar a la función `map()` de Python, pero las tareas se ejecutan en paralelo. Aquí tienes un ejemplo:

```python
from concurrent.futures import ThreadPoolExecutor

def tarea(n):
    return n * 2

with ThreadPoolExecutor() as executor:
    resultados = executor.map(tarea, [1, 2, 3, 4, 5])
    print(list(resultados))  # Imprime: [2, 4, 6, 8, 10]
```

