# List

## Values

- `list.append(_x_)`
- `list.extend(_iterable_)`: Extiende la lista agregándole todos los ítems del iterable
- `list.insert(i, x)`
- `list.remove(x)`
- `list.pop([i])`
- `list.clear()`
- `list.index(_x_[, _start_[, _end_]])`: Retorna el índice basado en cero del primer elemento cuyo valor sea igual a _x_. Lanza una excepción  "ValueError" si no existe tal elemento.
- `list.count(_x_)`
- `list.sort(_*_, _key=None_, _reverse=False_)`
- `list.reverse()`
- `list.copy()`
##Example
```python
fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
fruits.count('apple')
fruits.count('tangerine')
fruits.index('banana')
fruits.index('banana', 4)  # Find next banana starting at position 4
fruits.reverse()
fruits
fruits.append('grape')
fruits
fruits.sort()
fruits
fruits.pop()
```

## Lista como pila

```python
stack = [3, 4, 5]
stack.append(6)
stack.append(7)
stack

stack.pop()

stack

stack.pop()

stack.pop()

stack
```

## Lista como cola

```python
from collections import deque
queue = deque(["Eric", "John", "Michael"])
queue.append("Terry")           # Terry arrives
queue.append("Graham")          # Graham arrives
queue.popleft()                 # The first to arrive now leaves

queue.popleft()                 # The second to arrive now leaves

queue                           # Remaining queue in order of arrival
```

## Avanced list

### Compresiones de listas

>Las comprensiones de listas ofrecen una manera concisa de crear listas. Sus usos comunes son para hacer nuevas listas donde cada elemento es el resultado de algunas operaciones aplicadas a cada miembro de otra secuencia o iterable, o para crear un segmento de la secuencia de esos elementos para satisfacer una condición determinada.

```python
squares = []
for x in range(10):
    squares.append(x**2)

squares
#[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

#Usando lambda
squares = list(map(lambda x: x**2, range(10)))

#Forma consisa
squares = [x**2 for x in range(10)]
```

#### For and if
Una lista de comprensión consiste de corchetes rodeando una expresión seguida de la declaración `for` y luego cero o más declaraciones `for` o `if`. El resultado será una nueva lista que sale de evaluar la expresión en el contexto de los `for` o `if` que le siguen. Por ejemplo, esta lista de comprensión combina los elementos de dos listas si no son iguales:

```python
[(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]

#Equivalente
combs = []
for x in [1,2,3]:
	for y in [3,1,4]:
		if x != y:
             combs.append((x, y))
```

#### Uso con tuplas
Si la expresión es una tupla (como el `(x, y)` en el ejemplo anterior), debe estar entre paréntesis.
```python
vec = [-4, -2, 0, 2, 4]
# create a new list with the values doubled
[x*2 for x in vec]
#[-8, -4, 0, 4, 8]

# filter the list to exclude negative numbers
[x for x in vec if x >= 0]
#[0, 2, 4]

# apply a function to all the elements
[abs(x) for x in vec]
#[4, 2, 0, 2, 4]

# call a method on each element
freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
[weapon.strip() for weapon in freshfruit]
#['banana', 'loganberry', 'passion fruit']

# create a list of 2-tuples like (number, square)
[(x, x**2) for x in range(6)]

# the tuple must be parenthesized, otherwise an error is raised
[x, x**2 for x in range(6)]
  File "<stdin>", line 1
    [x, x**2 for x in range(6)]
     ^^^^^^^
SyntaxError: did you forget parentheses around the comprehension target?
# flatten a list using a listcomp with two 'for'
vec = [[1,2,3], [4,5,6], [7,8,9]]
[num for elem in vec for num in elem]
#[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### Funciones complejas

```python
from math import pi
[str(round(pi, i)) for i in range(1, 6)]
#['3.1', '3.14', '3.142', '3.1416', '3.14159']
```

#### Listas por compresion anidadas 

>La expresión inicial de una comprensión de listas puede ser cualquier expresión arbitraria, incluyendo otra comprensión de listas.
>
>Considerá el siguiente ejemplo de una matriz de 3x4 implementada como una lista de tres listas de largo 4.

```python
matrix = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12],
]
```

```python
[[row[i] for row in matrix] for i in range(4)]
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

```python
transposed = []
for i in range(4):
    transposed.append([row[i] for row in matrix])

transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]

#Equivalente
transposed = []
for i in range(4):
    # the following 3 lines implement the nested listcomp
    transposed_row = []
    for row in matrix:
        transposed_row.append(row[i])
    transposed.append(transposed_row)

transposed
```


## Matriz

```python
array=np.array([1,2,3])
matriz2d=np.array([[3,4,5],[2,3,4]])
matriz3d=np.array([[[2,3,4],[3,4,5]],[[2,3,4],[3,4,5]]])
```

## Funcion <font color="#d99694">del</font>

Hay una manera de quitar un ítem de una lista dado su índice en lugar de su valor: la instrucción [`del`](https://docs.python.org/es/3/reference/simple_stmts.html#del). Esta es diferente del método `pop()`, el cual retorna un valor. La instrucción `del` también puede usarse para quitar secciones de una lista o vaciar la lista completa (lo que hacíamos antes asignando una lista vacía a la rebanada). Por ejemplo:

```python
a = [-1, 1, 66.25, 333, 333, 1234.5]
del a[0]
a
#[1, 66.25, 333, 333, 1234.5]

del a[2:4]
a
#[1, 66.25, 1234.5]

del a[:]
a
#[]
```



# [[Tuplas y secuencias]]

# [[Conjuntos]]

# [[Diccionarios]]

# [[Desempaquetado]]

[5. Estructuras de datos — documentación de Python - 3.12.4](https://docs.python.org/es/3/tutorial/datastructures.html#sets)

