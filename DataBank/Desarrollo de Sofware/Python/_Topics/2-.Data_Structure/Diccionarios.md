Un diccionario en Python es una estructura de datos que permite almacenar y organizar elementos en pares clave-valor.

##### Caracteristicas

- `Elementos únicos`: Cada clave en un diccionario es única. No puede haber duplicados.
- `Mutables`: Puedes añadir, modificar y eliminar elementos de un diccionario

```python
tel = {'jack': 4098, 'sape': 4139}
 tel['guido'] = 4127
 tel
#{'jack': 4098, 'sape': 4139, 'guido': 4127}
 tel['jack']
#4098
 del tel['sape']
 tel['irv'] = 4127
 tel
#{'jack': 4098, 'guido': 4127, 'irv': 4127}
 list(tel)
#['jack', 'guido', 'irv']
 sorted(tel)
#['guido', 'irv', 'jack']
 'guido' in tel
#True
 'jack' not in tel
#False
```

#### dict
El constructor dict() crea un diccionario directamente desde secuencias de pares clave-valor:

```python
dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
{'sape': 4139, 'guido': 4127, 'jack': 4098}
```

#### Compress Dictionary

```python
{x: x**2 for x in (2, 4, 6)}
{2: 4, 4: 16, 6: 36}
```
