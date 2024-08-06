# Ejercicio #2

```python
!pip install pandas

datos = {'marcos':10,
         'luis':8,
         'jamon':5,
         'luisa':9,
         'maria':4,
         'elizabeth':10,
         'cocas':8}

def funcion(calificaciones):
    
    camo = pd.Series(calificaciones)
    maximo = camo.max()
    minimo = camo.min()
    media = camo.mean()
    desviacione = camo.std()
    
    camote = {'cali max:': maximo,
              'cali min:': minimo,
              'media:': media,
              'desviacion tipica:':desviacione}
    cal = pd.Series(camote)
    return cal

x = funcion(datos)
print(x)
```

# Ejercicio #3

```
import pandas as pd
import numpy as np
#Escribir una función que reciba un diccionario con las notas de los alumnos de un curso 
# y devuelva una serie con las notas de los alumnos aprobados ordenadas de mayor a menor.
calificaciones={"Pedro":10,"Lili":9,"Ana":5,"Gustabo":8}

def aprobados(diccionario):
    serie=pd.Series(diccionario)
    serie=serie[serie>6]
    return serie

print(aprobados(calificaciones))
```

# Ejercicio #4

```python
#Escribir programa que genere y muestre por pantalla un DataFrame con los datos de la tabla siguiente:

datos={"Mes":["Enero","Febrero","Marzo","Abril"],"Ventas":[30500,35600,28300,33900],"Gastos":[22000,23400,18100,20700]}
df=pd.DataFrame(datos)

df
```

# Ejercicio #6

```python
#El fichero cotizacion.csv contiene las cotizaciones de las empresas del IBEX35 con las siguientes columnas: 
# nombre (nombre de la empresa), Final (precio de la acción al cierre de bolsa), Máximo (precio máximo de la acción durante la jornada), 
# Mínimo (precio mínimo de la acción durante la jornada), volumen (Volumen al cierre de bolsa), 
# Efectivo (capitalización al cierre en miles de euros). 
# Construir una función que construya un DataFrame a partir del un fichero con el formato anterior 
# y devuelva otro DataFrame con el mínimo, el máximo y la media de dada columna.
import pandas as pd

def resumen_cotizaciones(fichero):
    df = pd.read_csv(fichero, sep=';', decimal=',', thousands='.', index_col=0)
    return pd.DataFrame([df.min(), df.max(), df.mean()], index=['Mínimo', 'Máximo', 'Media'])

resumen_cotizaciones("cotizacion.csv")
```

# Ejercicio #7

```python
df = pd.read_csv("titanic.csv",index_col="PassengerId")

altura,ancho=df.shape
cantidadTotal=int(altura)*int(ancho)
print(f"Dimensiones: {df.shape}")
print(f"Cantidad de datos: {cantidadTotal}")
#print(df.dtypes)
#df.head(10)
#df.tail(10)
```

```python
#Mostrar por pantalla los datos del pasajero con identificador 148.
df.loc[148,:]
```

```python
#Mostrar por pantalla el porcentaje de personas que sobrevivieron y murieron.
muertos=len(df[df["Survived"]==1])
vivos=len(df[df["Survived"]==0])

porcentajeVivos=100-((vivos*100)/altura)
porcentajeMuertos=100-((muertos*100)/altura)

print(f"Vivos: {round(porcentajeVivos,2)}% porcentajeMuertos: {round(porcentajeMuertos,2)}%")
```

```python
#Mostrar por pantalla los nombres de las personas que iban en primera clase ordenadas alfabéticamente.

datos=df.loc[df["Pclass"]==1,["Name"]]
datos.sort_values("Name")

#Alternativa
print(titanic[titanic["Pclass"]==1]['Name'].sort_values())
```

```python
#Mostrar por pantalla el porcentaje de personas que sobrevivieron en cada clase.
vivosPrimera=((len(df[(df["Survived"]==1) & (df["Pclass"]==1)])*100)/altura)
vivosSegunda=((len(df[(df["Survived"]==1) & (df["Pclass"]==2)])*100)/altura)
vivosTercera=((len(df[(df["Survived"]==1) & (df["Pclass"]==3)])*100)/altura)

print(f"Vivos primera clase: {round(vivosPrimera,2)}%")
print(f"Vivos segunda clase: {round(vivosSegunda,2)}%")
print(f"Vivos tercera clase: {round(vivosTercera,2)}%")

#Alternativa

# Mostrar por pantalla el porcentaje de personas que sobrevivieron y murieron
print(titanic['Survived'].value_counts()/titanic['Survived'].count() * 100)

# Alternativa
print(titanic['Survived'].value_counts(normalize=True) * 100)
```

```python
#Eliminar del DataFrame los pasajeros con edad desconocida.

df.dropna()

#Respuesta
# Eliminar del DataFrame los pasajeros con edad desconocida.
titanic.dropna(subset=['Age'])
```

```python
#Mostrar por pantalla la edad media de las mujeres que viajaban en cada clase.

edadMediaMujeres=df.loc[df["Sex"]=="female","Age"].mean()

print("Edad media mujeres: ",round(edadMediaMujeres,2))

#Alternativa
# Mostrar la edad media de las mujeres que viajaban en cada clase.
print(titanic.groupby(['Pclass','Sex'])['Age'].mean().unstack()['female'])
```

```python
#Añadir una nueva columna booleana para ver si el pasajero era menor de edad o no.

def esMenor(datos):
    
    if datos>=18:
        return 1
    else:
        return 0

df["Minor"]=df["Age"].apply(esMenor)    

df

#Alternativa mucho mejor
# Añadir una nueva columna booleana para ver si el pasajero era menor de edad o no.
titanic['Young'] = titanic['Age'] < 18
```

```python
# Mostrar por pantalla las filas pares del DataFrame.
print(titanic.iloc[range(0,titanic.shape[0],2)])
```

```python
#Mostrar por pantalla el porcentaje de personas que sobrevivieron en cada clase
print(titanic.groupby('Pclass')['Survived'].value_counts(normalize=True))
```

```python

#Mostrar por pantalla el porcentaje de menores y mayores de edad que sobrevivieron en cada clase.

cantMayores=len(df[(df["Minor"]==0) & (df["Survived"]==1)])
cantMenores=len(df[(df["Minor"]==1) & (df["Survived"]==1)])
porCantMenores=(cantMenores*100)/altura
porCantMayores=(cantMayores*100)/altura

print(f"Menores{porCantMenores}% Mayores:{porCantMayores}")

# Mostrar el porcentaje de menores y mayores de edad que sobrevivieron en cada clase.
print(titanic.groupby(['Pclass', 'Young'])['Survived'].value_counts(normalize = True) * 100)
```

# Ejercicio #8

```python
#Generar un DataFrame con los datos de los cuatro ficheros.
import pandas as pd
import numpy as np
import datetime as dt

df1=pd.read_csv("emisiones-2017.csv",sep=';')
df2=pd.read_csv("emisiones-2017.csv",sep=';')
df3=pd.read_csv("emisiones-2017.csv",sep=';')
df4=pd.read_csv("emisiones-2017.csv",sep=';')

emisiones=pd.concat([df1,df2,df3,df4])
emisiones
```

```python
#Filtrar las columnas del DataFrame para quedarse con las columnas ESTACION, MAGNITUD, AÑO, MES y 
# las correspondientes a los días D01, D02, etc.

columnas = ['ESTACION', 'MAGNITUD', 'ANO', 'MES']
columnas.extend([col for col in emisiones if col.startswith('D')]) #Agregara todas las columnas que  terminenen en D
emisiones = emisiones[columnas]
emisiones
```

### Extends

- El método **`extend`** se utiliza para agregar múltiples elementos a una lista.
- A diferencia del método **`append`**, que agrega un solo elemento al final de la lista, **`extend`** agrega cada elemento de una iterable (en este caso, una lista) al final de la lista.
- En este contexto, **`extend`** se usa para agregar todas las columnas del DataFrame que comienzan con **`'D'`** a la lista **`columnas`**. Esto asegura que las columnas correspondientes a los días específicos se añadan a la lista de columnas que se conservarán en el DataFrame final.

```python
# Reestructurar el DataFrame para que los valores de los contaminantes de las columnas de los días aparezcan en una única columna.
emisiones = emisiones.melt(id_vars=['ESTACION', 'MAGNITUD', 'ANO', 'MES'], var_name='DIA', value_name='VALOR')
emisiones
```

### Melt

La función **`melt()`** es una operación comúnmente utilizada en la manipulación y transformación de datos en pandas (una biblioteca de Python para análisis de datos). Básicamente, su propósito es "derretir" o "reorganizar" el DataFrame para convertirlo de un formato ancho a un formato largo, facilitando así su manipulación y análisis. En el ejemplo que proporcionaste, la función **`melt()`** se utiliza de la siguiente manera:

- **`emisiones.melt()`**: Esto aplica la función **`melt()`** al DataFrame **`emisiones`**.
- **`id_vars=['ESTACION', 'MAGNITUD', 'ANO', 'MES']`**: Este argumento especifica las columnas que no se van a "derretir", es decir, las columnas que se mantendrán intactas en su forma actual. Estas columnas se considerarán como identificadores únicos para cada fila en el nuevo DataFrame resultante.
- **`var_name='DIA'`**: Este argumento especifica el nombre de la nueva columna que contendrá los nombres de las columnas que se "derriten". En este caso, se llamará **`'DIA'`**.
- **`value_name='VALOR'`**: Este argumento especifica el nombre de la nueva columna que contendrá los valores de las columnas que se "derriten". En este caso, se llamará **`'VALOR'`**.

```python
#Añadir una columna con la fecha a partir de la concatenación del año, el mes y el día (usar el módulo datetime).

# Crear una nueva columna con las fechas a partir del año, mes y día
# Primero eliminamos el caracter D del comienzo de la columna de los días
emisiones['DIA'] = emisiones.DIA.str.strip('D')
# Concatenamos las columnas del año, mes y día
emisiones['FECHA'] = emisiones.ANO.apply(str) + '/' + emisiones.MES.apply(str) + '/' + emisiones.DIA.apply(str)
# Convertimos la nueva columna al tipo fecha
emisiones['FECHA'] = pd.to_datetime(emisiones.FECHA, format='%Y/%m/%d', infer_datetime_format=True, errors='coerce')
emisiones
```

### pd.to_datetime

Los argumentos **`format`**, **`infer_datetime_format`** y **`errors`** son opciones para controlar cómo se interpreta y maneja el formato de la fecha. En este caso, se especifica explícitamente el formato como '%Y/%m/%d', que coincide con el formato de la cadena que creamos anteriormente. El argumento **`errors='coerce'`** se utiliza para manejar cualquier error que pueda surgir durante la conversión, asignando valores nulos (**`NaT`**) a las filas que no se puedan convertir correctamente.

```
#Eliminar las filas con fechas no válidas (utilizar la función isnat del módulo numpy) 
# y ordenar el DataFrame por estaciones contaminantes y fecha.

# Eliminar las filas con fechas no válidas
emisiones = emisiones.drop(emisiones[np.isnat(emisiones.FECHA)].index)#Borra ese index basado en isnat en la variable de emisiones Fecha
# Ordenar el el dataframe por estación, magnitud y fecha
emisiones.sort_values(['ESTACION', 'MAGNITUD', 'FECHA'])
```
### ![[Datos faltantes#Isnat]]
### Unique

Sirve pa sacar todos los datos existentes en una columna

```python
#Crear una función que reciba una estación, un contaminante y un rango de fechas y 
# devuelva una serie con las emisiones del contaminante dado en la estación y rango de fechas dado.
#def serieEmisiones (estacion,magnitud,fechaFin,fechaInc):
   #for fecha in range((fechaFin - fechaInc).days + 1):
       #nuevodf=emisiones.loc[(emisiones["ESTACION"]==estacion)&(emisiones["MAGNITUD"]==magnitud)&(emisiones["FECHA"]==fecha,:]
    
       #return nuevodf 
   # Función que devuelve las emisiones de un contaminante dado en una estación y rango de fechas dado.
   
def evolucion(estacion, contaminante, desde, hasta):
    return emisiones[(emisiones.ESTACION == estacion) & (emisiones.MAGNITUD == contaminante) & (emisiones.FECHA >= desde) & (emisiones.FECHA <= hasta)].sort_values('FECHA').VALOR
evolucion(56, 8, dt.datetime.strptime('2018/10/25', '%Y/%m/%d'), dt.datetime.strptime('2019/02/12', '%Y/%m/%d'))
    
#print(serieEmisiones(4,6,'2017-01-01','2019-01-01'))
```

```python
#Mostrar un resumen descriptivo (mínimo, máximo, media, etc.) para cada contaminante.

# Resumen descriptivo por contaminantes
emisiones.groupby('MAGNITUD').VALOR.describe()
```

```python
#Mostrar un resumen descriptivo para cada contaminante por distritos.

# Resumen descriptivo por contaminantes y distritos
emisiones.groupby(['ESTACION', 'MAGNITUD']).VALOR.describe()
```
![[Pasted image 20240703094313.png|475]]

```python
def resumen(estacion, contaminante):
    return emisiones[(emisiones.ESTACION == estacion) & (emisiones.MAGNITUD == contaminante)].VALOR.describe()

# Resumen de Dióxido de Nitrógeno en Plaza Elíptica
print('Resumen Dióxido de Nitrógeno en Plaza Elíptica:\\n', resumen(56, 8),'\\n', sep='')
# Resumen de Dióxido de Nitrógeno en Plaza del Carmen
print('Resumen Dióxido de Nitrógeno en Plaza del Carmen:\\n', resumen(35, 8), sep='')
```

![[Pasted image 20240703094340.png]]

## Unstack()

El método **`unstack()`** en pandas se utiliza para "desapilar" una columna de índice en un DataFrame y convertirla en columnas. Esto es útil cuando tienes un DataFrame con un índice jerárquico y deseas convertir una parte de ese índice en columnas.

En tu función **`evolucion_mensual`**, después de agrupar los datos por **`'ESTACION'`** y **`'MES'`**, se aplica el método **`unstack('MES')`** para desapilar el índice **`'MES'`**, convirtiendo así los valores únicos de **`'MES'`** en columnas.

#Ejercicios 