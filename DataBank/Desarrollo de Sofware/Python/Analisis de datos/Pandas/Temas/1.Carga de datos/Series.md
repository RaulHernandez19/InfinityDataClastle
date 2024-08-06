Estructura de una dimension similares a los arrays.

Son **homogéneas**, es decir, sus elementos tienen que ser del mismo tipo, y su **tamaño es inmutable**, es decir, no se puede cambiar, aunque si su contenido.

Dispone de un **índice que asocia un nombre a cada elemento del la serie**, a través de la cuál se accede al elemento.

![[Pasted image 20240625142210.png]]

## **Creación**

### <font color="#4f81bd">A partir de una lista</font>

`Series(data=lista, index=indices, dtype=tipo)` : Devuelve un objeto de tipo Series con los datos de la lista `lista`, las filas especificados en la lista `indices` y el tipo de datos indicado en `tipo`

![[Pasted image 20240625142300.png]]

### <font color="#4f81bd">A partir de un diccionario</font>

`Series(data=diccionario, index=indices)`: Devuelve un objeto de tipo Series con los valores del diccionario `diccionario` y las filas especificados en la lista `indices`. Si no se pasa la lista de índices se utilizan como índices las claves del diccionario.

![[Pasted image 20240625142329.png]]
## Atributos

- `s.size` : Devuelve el número de elementos de la serie `s`.
- `s.index` : Devuelve una lista con los nombres de las columbas del DataFrame `s`.
- `s.dtype` : Devuelve el tipo de datos de los elementos de la serie `s`.

![[Pasted image 20240625142422.png]]
## Acceso

### Por posición e índice

![[Pasted image 20240625142445.png]]

## Funciones

- `s.count()` : Devuelve el número de elementos que no son nulos ni `NaN` en la serie `s`.
- `s.sum()` : Devuelve la suma de los datos de la serie `s` cuando los datos son de un tipo numérico, o la concatenación de ellos cuando son del tipo cadena `str`.
- `s.cumsum()` : Devuelve una serie con la suma acumulada de los datos de la serie `s` cuando los datos son de un tipo numérico.
- `s.value_counts()` : Devuelve una serie con la frecuencia (número de repeticiones) de cada valor de la serie `s`.
- `s.min()` : Devuelve el menor de los datos de la serie `s`.
- `s.max()` : Devuelve el mayor de los datos de la serie `s`.
- `s.mean()` : Devuelve la media de los datos de la serie `s` cuando los datos son de un tipo numérico.
- `s.var()` : Devuelve la varianza de los datos de la serie `s` cuando los datos son de un tipo numérico.
- `s.std()` : Devuelve la desviación típica de los datos de la serie `s` cuando los datos son de un tipo numérico.
- `s.describe()`: Devuelve una serie con un resumen descriptivo que incluye el número de datos, su suma, el mínimo, el máximo, la media, la desviación típica y los cuartiles.

## Filtrar

`s[condicion]` : Devuelve una serie con los elementos de la serie `s` que se corresponden con el valor `True` de la lista booleana `condicion`. `condicion` debe ser una lista de valores booleanos de la misma longitud que la serie.

![[Pasted image 20240625142509.png]]
## Ordenar

`s.sort_values(ascending=booleano`) : Devuelve la serie que resulta de ordenar los valores la serie `s`. Si argumento del parámetro `ascending` es `True` el orden es creciente y si es `False` decreciente.

`df.sort_index(ascending=booleano`) : Devuelve la serie que resulta de ordenar el índice de la serie `s`. Si el argumento del parámetro `ascending` es `True` el orden es creciente y si es `False` decreciente.

![[Pasted image 20240625142525.png]]