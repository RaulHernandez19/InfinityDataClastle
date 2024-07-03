# Eliminar filas o columnas con datos vacíos

Con **dropna()** se borraran los datos vacios del dataframe.
![[Pasted image 20240625144512.png]]
![[Pasted image 20240625144524.png]]
# Detectar datos vacios

Se utiliza **isnull(),** que detecta true cuando esta vacio un espacio.

![[Pasted image 20240625144553.png]]

La suma total de toods los datos vacios en la columna apellido

# Rellenar columnas vacías

Se utiliza fillna(), primero accediendo a una o mas columnas, para después poner fillna y poner por que será remplazado ese espacio vacío.

Importante mencionar que lo que hace es generar una columna con dichos datos remplazados, por lo que no es que cambie como tal el df ya existente.

![[Pasted image 20240625144615.png]]

### Rellenar columnas con un valor predeterminado con un diccionario

![[Pasted image 20240625144630.png]]

# Isnat 

En este caso, se utiliza la función **`np.isnat()`** del módulo NumPy para identificar y eliminar las filas que contienen fechas no válidas en la columna **`'FECHA'`**. La razón principal para usar **`np.isnat()`** en lugar de **`dropna()`** es que **`dropna()`** se utiliza comúnmente para eliminar filas que contienen valores **`NaN`** (valores nulos), mientras que **`np.isnat()`** se utiliza específicamente para identificar valores que no son fechas válidas en objetos datetime.

La función **`dropna()`** eliminaría todas las filas que contienen valores nulos en cualquier columna, lo cual puede no ser lo que queremos si solo estamos interesados en eliminar las filas con fechas no válidas en la columna **`'FECHA'`**.

Por otro lado, **`np.isnat()`** devuelve una máscara booleana que indica si cada valor en la serie de fechas es un valor **`NaT`** (Not a Time) o no. De esta manera, podemos usar esta máscara para filtrar las filas del DataFrame **`emisiones`** que contienen fechas no válidas en la columna **`'FECHA'`**, eliminándolas correctamente.

```python
#Mostrar por pantalla las estaciones y los contaminantes disponibles en el DataFrame.

# Mostrar las estaciones disponibles
print('Estaciones:', emisiones.ESTACION.unique())
# Mostrar los contaminantes disponibles
print('Contaminantes:', emisiones.MAGNITUD.unique())
```