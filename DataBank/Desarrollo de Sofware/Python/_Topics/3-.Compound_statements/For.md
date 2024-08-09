La sentencia for se usa para iterar sobre los elementos de una secuencia (como una cadena de caracteres, tupla o lista) u otro objeto iterable.

La funcion [[range()]] es de las mas comunes para iterar un rango especifico.
```python
for i in range(10):
    print(i)
    i = 5
```

La sentencia [[break]] ejecutada en la primera suite termina el bucle sin ejecutar el conjunto de cláusulas else. La sentencia [[continue]] ejecutada en la primera suite omite el resto de las cláusulas y continúa con el siguiente elemento, o con la cláusula else si no hay un elemento siguiente.

### For avanzado

#### Uso con [[zip()]]

Puedes usar `zip()` dentro de un bucle `for` y agregar una condición para realizar acciones específicas basadas en el contenido de los iterables.
```python
nombres = ["Ana", "Luis", "Juan", "Marta"]
edades = [23, 35, 19, 28]

for nombre, edad in zip(nombres, edades):
    if edad > 25:
        print(f"{nombre} tiene más de 25 años.")
```




