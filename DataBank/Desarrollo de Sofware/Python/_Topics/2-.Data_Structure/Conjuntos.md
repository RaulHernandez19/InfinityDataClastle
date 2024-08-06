Es una colección no ordenada y sin elementos repetidos. Los usos básicos de éstos incluyen verificación de pertenencia y eliminación de entradas duplicadas. Los conjuntos también soportan operaciones matemáticas como la unión, intersección, diferencia, y diferencia simétrica.

```python
mi_conjunto = {1, 2, 3}
```

##### Caracteristicas

- `Desordenados`: Los elementos de un conjunto no están en ningún orden en particular.
- `Elementos únicos`: Cada elemento en un conjunto es único. No puede haber duplicados.
- `Mutables`: Puedes añadir y eliminar elementos de un conjunto.

>Las llaves o la función set() pueden usarse para crear conjuntos. Notá que para crear un conjunto vacío tenés que usar set(), no {}; esto último crea un diccionario vacío, una estructura de datos que discutiremos en la sección siguiente.

```python
basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
 print(basket)                      # show that duplicates have been removed
#{'orange', 'banana', 'pear', 'apple'}
 'orange' in basket                 # fast membership testing
#True
 'crabgrass' in basket
#False

 # Demonstrate set operations on unique letters from two words

 a = set('abracadabra')
 b = set('alacazam')
 a                                  # unique letters in a
#{'a', 'r', 'b', 'c', 'd'}
 a - b                              # letters in a but not in b
#{'r', 'd', 'b'}
 a | b                              # letters in a or b or both
#{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
 a & b                              # letters in both a and b
#{'a', 'c'}
 a ^ b                              # letters in a or b but not both
#{'r', 'd', 'b', 'm', 'z', 'l'}
```
## Compresion de conjuntos
```python
a = {x for x in 'abracadabra' if x not in 'abc'}
a
#{'r', 'd'}
```

## Ejemplos utiles

### Eliminar duplicados
```python
lista_con_duplicados = [1, 2, 2, 3, 4, 4, 5, 5]
conjunto = set(lista_con_duplicados)
lista_sin_duplicados = list(conjunto)
print(lista_sin_duplicados)  # Resultado: [1, 2, 3, 4, 5]

```

### Pruebas de pertenecias

```python
conjunto = {1, 2, 3, 4, 5}
print(3 in conjunto)  # Resultado: True
print(6 in conjunto)  # Resultado: False

```

### Creacion a partir de lista

```python
lista = [1, 2, 2, 3, 4, 4, 5, 5]
conjunto = set(lista)
print(conjunto)  # Resultado: {1, 2, 3, 4, 5}
```