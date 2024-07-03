La mezcla de DataFrames permite integrar filas de dos DataFrames que contienen información en común en una o varias columnas o índices que se conocen como _clave_.

Para mezclar dos DataFrames se utiliza el siguiente método:

- `df.merge(df1, df2, on = clave, how = tipo)`: Devuelve el DataFrame que resulta de mezclar el DataFrame `df2` con el DataFrame `df1`, usando como claves las columnas de la lista `clave` y siguiendo el método de mezcla indicado por `tipo`.

## Inner

`"inner"` (por defecto): El DataFrame resultante solo contiene las filas cuyos valores en la clave están en los dos DataFrames. Es equivalente a la intersección de conjuntos.

```python
import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"],  "Sexo":["Mujer", "Hombre", "Mujer"]})
>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro", "Luis"], "Edad":[25, 30, 18]]})
>>> df = pd.merge(df1, df2, on="Nombre")
>>> print(df)
  Nombre    Sexo  Edad
0   Luis  Hombre    18
1  María   Mujer    25
```

## Outer

`"outer"`: El DataFrame resultante contiene todas las filas de los dos DataFrames. Si una fila de un DataFrame no puede emparejarse con otra los mismos valores en la clave en el otro DataFrame, la fila se añade igualmente al DataFrame resultante rellenando las columnas del otro DataFrame con el valor `NaN`. Es equivalente a la unión de conjuntos.

```python
>>> import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"],  "Sexo":["Mujer", "Hombre", "Mujer"]})
>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro", "Luis"], "Edad":[25, 30, 18]]})
>>> df = pd.merge(df1, df2, on="Nombre", how="outer")
>>> print(df)
   Nombre    Sexo  Edad
0  Carmen   Mujer   NaN
1    Luis  Hombre  18.0
2   María   Mujer  25.0
3   Pedro     NaN  30.0
```

## Left

`"left"`: El DataFrame resultante contiene todas las filas del primer DataFrame y descarta las filas del segundo DataFrame que no pueden emparejarse con alguna fila del primer DataFrame a través de la clave.

```python
>>> import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"],  "Sexo":["Mujer", "Hombre", "Mujer"]})
>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro", "Luis"], "Edad":[25, 30, 18]]})
>>> df = pd.merge(df1, df2, on="Nombre", how="left")
>>> print(df)
   Nombre    Sexo  Edad
0  Carmen   Mujer   NaN
1    Luis  Hombre  18.0
2   María   Mujer  25.0
```

## Right

`"right"`: El DataFrame resultante contiene todas las filas del segundo DataFrame y descarta las filas del primer DataFrame que no pueden emparejarse con alguna fila del segundo DataFrame a través de la clave.

```python
>>> import pandas as pd
>>> df1 = pd.DataFrame({"Nombre":["Carmen", "Luis", "María"],  "Sexo":["Mujer", "Hombre", "Mujer"]})
>>> df2 = pd.DataFrame({"Nombre":["María", "Pedro", "Luis"], "Edad":[25, 30, 18]]})
>>> df = pd.merge(df1, df2, on="Nombre", how="right")
>>> print(df)
  Nombre    Sexo  Edad
0  María   Mujer    25
1  Pedro     NaN    30
2   Luis  Hombre    18
```