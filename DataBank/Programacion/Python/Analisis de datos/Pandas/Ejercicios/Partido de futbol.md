```python
import pandas as pd

df_fixture=pd.read_csv("fifa_worldcup_fixture.csv")
df_matches=pd.read_csv("fifa_worldcup_matches.csv")
df_missing=pd.read_csv("fifa_worldcup_missing_data.csv")
```

```python
#Limpiando df_fixture borrando los espacio en blanco en las variables string
df_fixture["home"]=df_fixture["home"].str.strip()
df_fixture["away"]=df_fixture["away"].str.strip()

#Limpiando df_missing 
df_missing[df_missing["home"].isnull()] #Detectamos las filas vacias
df_missing.dropna(inplace=True) #Aqui se borra la data faltante y con inplace se guardan los datos
```

```python
#Agregando la data faltante a la data historica
pd_matches=pd.concat([df_missing,df_matches],ignore_index=True)#Ayuda a que los index originales son 
#ignorados y se enumera de 0
```

```python
#Limpiamos df_matches los datos duplicados
df_matches.drop_duplicates(inplace=True)
df_matches.sort_values("year",inplace=True)
```

```python
#Limpiando mas el df_matches
#Buscamos esta anomalia
#score_groups=df_matches.groupby('score').groups

#La mejor forma, analizando los grupos de conjuntos de score
#for score,indices in score_groups.items():
    #print(f"Grupo {score} indice: {indices}")
```

```python
#Encontramos el index del dato anomalo y lo borramos
index_borrar=df_matches[df_matches['score'].str.contains("w")].index

df_matches.drop(index=index_borrar, inplace=True)
```

```python
#En busca de mas datos anomalos
df_matches[df_matches["score"].str.contains('[^\\d–]')]

df_matches["score"]=df_matches["score"].str.replace('[^\\d–]','',regex=True)

#df_matches[df_matches["score"].str.contains("a")]
```

```python
#Limpieza de espacios en blanco por si acaso
df_matches["home"]=df_matches["home"].str.strip()
df_matches["away"]=df_matches["away"].str.strip()
```

```python
#Crear dos nuevas columnas a partir de score
df_matches[['homeScore','awayScore']]=df_matches["score"].str.split("–",expand=True)
df_matches
#Eliminar score antiguo
#Renombramosdf_matches.drop('score',axis=1, inplace=True)
```

```python
df_matches.rename(columns={'home':'HomeTeam','away':'AwayTeam','year':'Year'},inplace=True)
```

```python
#Reviso los tipos de datos y homeScore y awayScore son string
df_matches.dtypes
df_matches=df_matches.astype({'homeScore':int,'awayScore':int})
df_matches.dtypes
```

```python
#Agregamos una nueva columna
df_matches["totalGoals"]=df_matches["homeScore"]+df_matches["awayScore"]
df_matches
```

```python
#Exportando por fin
df_matches.to_csv("clean_fifa_worldcup_matches.csv",index=False) #No exportamos los index
```

```python
#Comprobando datos viendo cuantos partidos han jugado en cada mundial

#grupos=df_matches.groupby("Year").groups#sacamos los años sin repetir

#for anio,partidos in grupos.items():
   # print(anio,len(df_matches[df_matches["Year"]==anio] ))
years=[1998,2002,2006,2010,2014,2018]
for year in years:
    print(year,len(df_matches[df_matches["Year"]==year]))
```

#Ejercicios 