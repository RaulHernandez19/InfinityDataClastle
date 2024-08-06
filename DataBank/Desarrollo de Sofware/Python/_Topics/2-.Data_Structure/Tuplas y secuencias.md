En Python, una tupla es una estructura de datos que puede contener elementos de diferentes tipos1. Aquí te dejo algunos detalles importantes sobre las tuplas:

```python
mi_tupla = (1, 2, 3, 4, 5)
```
##### Caracteristicas 

- `Ordenadas`: Los elementos de una tupla están ordenados y mantienen el orden en el que se añadieron.
- `Inmutables`: Una vez creada, no se pueden modificar sus elementos2. Esto significa que no puedes añadir, modificar o eliminar elementos de una tupla después de su creación.
- `Versátiles`: Una tupla puede contener elementos de diferentes tipos de datos, como enteros, cadenas, flotantes, u otras tuplas.
- `Útiles`: Las tuplas son útiles cuando se necesita almacenar una colección de elementos que no van a cambiar a lo largo del tiempo. Además, las tuplas pueden ser utilizadas como claves en diccionarios, ya que al ser inmutables, garantizan que no cambiarán su valor a lo largo del tiempo.

## Example
```python
t = 12345, 54321, 'hello!'
t[0]
#12345
t
#(12345, 54321, 'hello!')

# Tuples may be nested:
u = t, (1, 2, 3, 4, 5)
u
#((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))

# Tuples are immutable:
t[0] = 88888

# but they can contain mutable objects:
v = ([1, 2, 3], [3, 2, 1])
v
#([1, 2, 3], [3, 2, 1])
```

## [[Desempaquetado]] inverso de tuplas
```python
x, y, z = t
```
