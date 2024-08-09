La función `zip()` en Python es una función incorporada que toma iterables (como listas, tuplas, etc.) y los agrega en pares ordenados, creando un nuevo iterable (generalmente una lista de tuplas). Cada tupla contiene elementos que ocupan la misma posición en los iterables originales.
#### Sintaxis
```python
zip(iterable1, iterable2, ...)
```

```python
nombres = ["Ana", "Luis", "Juan"]
edades = [23, 35, 19]

resultado = zip(nombres, edades)
print(list(resultado))

#[('Ana', 23), ('Luis', 35), ('Juan', 19)]
```
#### Desempaquetado de zip()
```python
pares = [('Ana', 23), ('Luis', 35), ('Juan', 19)] 
nombres, edades = zip(*pares) 
print(nombres) # ('Ana', 'Luis', 'Juan') 
print(edades) # (23, 35, 19)
```

```python
x = [1, 2, 3]
y = [4, 5, 6]
list(zip(x, y))
#[(1, 4), (2, 5), (3, 6)]
x2, y2 = zip(*zip(x, y))
x == list(x2) and y == list(y2)
#True
```

#### Creacion de diccionario

```python
nombres = ["Ana", "Luis", "Juan"] 
edades = [23, 35, 19] 
diccionario = dict(zip(nombres, edades)) print(diccionario)
#{'Ana': 23, 'Luis': 35, 'Juan': 19}
```


