## Dia #1

```python
#Sampe sirve para traer muestras aleatorias de el df
sf_permits.sample(10)
```

Obtenemos la cantidad de datos vacios y despues sacamos un promedio de los datos vacios que existen.

```python
# get the number of missing data points per column
missing_values_count = nfl_data.isnull().sum()

# look at the # of missing points in the first ten columns
missing_values_count[0:10]
----

# how many total missing values do we have?
total_cells = np.product(nfl_data.shape) #Aqui saca el total de celdas multiplicando el shape
total_missing = missing_values_count.sum()#Aqui suma todos los valores del missing values count

# percent of data that is missing
(total_missing/total_cells) * 100
```

Aqui hacemos una prueba de que pasaria si borraramos todas las filas que esten vacias

```python
# Your turn! Try removing all the rows from the sf_permits dataset that contain missing values. How many are left?
columns_with_na_dropped = sf_permits.dropna(axis=0)

print("Columns in original dataset: %d \\n" % sf_permits.shape[0])
print("Columns with na's dropped: %d" % columns_with_na_dropped.shape[0])
```

Aca rellenaremos

```python
# get a small subset of the NFL dataset
subset_nfl_data = nfl_data.loc[:, 'EPA':'Season'].head() #Forma de ur de una columna a una columna
subset_nfl_data
```

```python
# replace all NA's the value that comes directly after it in the same column, 
# then replace all the reamining na's with 0
subset_nfl_data.fillna(method = 'bfill', axis=0).fillna(0) #El metodo
#bfill lo que hara es llenar el dato vacio con el siguiente, y en cuyo caso que tambien sea vacio, se remplazara con 0 por si acaso
```

## Dia #2 Scaling and Normalization

```python
# modules we'll use
import pandas as pd
import numpy as np

# for Box-Cox Transformation
from scipy import stats

# for min_max scaling
from mlxtend.preprocessing import minmax_scaling

# plotting modules #Esta parte sirve para hacer graficos
import seaborn as sns
import matplotlib.pyplot as plt

# read in all our data
kickstarters_2017 = pd.read_csv("../input/kickstarter-projects/ks-projects-201801.csv")

# set seed for reproducibility
np.random.seed(0)

kickstarters_2017
```

Seed: genera una cantidad de numeros aleatorios , para que esa misma muestra pueda ser replicable despues.

### Scaling

## Dia #3 Parsing dates

```python
import pandas as pd
import numpy as np
import seaborn as sns
import datetime

# read in our data
earthquakes = pd.read_csv("../input/earthquake-database/database.csv")
landslides = pd.read_csv("../input/landslide-events/catalog.csv")
volcanos = pd.read_csv("../input/volcanic-eruptions/database.csv")

# set seed for reproducibility
np.random.seed(0)
```

```python
# print the first few rows of the date column
print(landslides['date'].head())
```
![[Pasted image 20240703094543.png]]

```python
# check the data type of our date column
landslides['date'].dtype
```

```python
dtype('O')
```

Ahora pasamos la clumna date a tio date

```python
# create a new column, date_parsed, with the parsed dates
landslides['date_parsed'] = pd.to_datetime(landslides['date'], format = "%m/%d/%y")
```

```python
earthquakes['date_parsed']=pd.to_datetime(earthquakes['Date'], infer_datetime_format = True)
#Usamos lo de abajo si marca error con el formato
#infer_datetime_format = True
```

```python
# get the day of the month from the date_parsed column
day_of_month_landslides = landslides['date_parsed'].dt.day
```

```python
day_of_month_landslides = landslides['date_parsed'].dt.day
day_of_month_landslides.head()
----
0     2.0
1    22.0
2     6.0
3    14.0
4    15.0
```

```python
# remove na's
day_of_month_landslides = day_of_month_landslides.dropna()

# plot the day of the month
sns.distplot(day_of_month_landslides, kde=False, bins=31)
```

![[Pasted image 20240703094647.png]]

#Ejercicios 