### Funciones

<font color="#d99694">EVALUATE</font>: Sirve para evaluar una funcion en el data set de forma simulada en DAX QUERY view.

<font color="#d99694">RANKX</font>: La función `RANKX` se utiliza para calcular el rango de cada fila dentro de un conjunto de datos. En este caso, está calculando el rango basado en la columna `FechaCreacion` en orden descendente (de la fecha más reciente a la más antigua)

```d
RANKX(
            FILTER(
             
            ),

            'DataBase'[FechaCreacion],

            ,

            DESC
```

<font color="#d99694">FILTER</font>: La función `FILTER` crea una tabla temporal que contiene solo las filas que cumplen con ciertas condiciones.

<font color="#d99694">EARLIER</font>: La función `EARLIER` se utiliza para referirse al valor de una columna en la fila actual del contexto de la fila externa. En este caso, se usa para comparar el `Num` de la fila actual con las filas dentro del filtro.

```d
`DataBase'[Num] = EARLIER('DataBase'[Num])`: 
```
Esto asegura que solo se consideren filas con el mismo `NumLote` que la fila actual.

<font color="#d99694">CONTAINSSTRING</font>: 
```d 
CONTAINSSTRING('DataBase'[Name], "TEXT") 
```