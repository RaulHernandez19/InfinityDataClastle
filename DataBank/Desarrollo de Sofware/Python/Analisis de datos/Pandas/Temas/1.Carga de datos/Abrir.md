![[Pasted image 20240625141620.png]]
# Abrir archivos

![[Pasted image 20240625141722.png]]

De esta forma lo abrimos con formato usando **JUPYTER** sin usar el print

![[Pasted image 20240625141732.png]]

Realmente el “archivo” que estamos abriendo en un **dataframe,** el mismo que estará compuesto por columnas y filas.
## Abrir archivos con nombres de las columnas mod

![[Pasted image 20240625141746.png]]

|                      |                                                                                               |
| -------------------- | --------------------------------------------------------------------------------------------- |
| ruta_archivo_o_búfer | URL o ubicación del directorio del archivo                                                    |
| sep                  | Significa separador, el valor predeterminado es ‘,’ como en csv (valores separados por comas) |
| index_col            | Hace que la columna pasada sea un índice en lugar de 0, 1, 2, 3…r                             |
| encabezamiento       | Hace pasada la fila/s[int/int list] como encabezado                                           |
| use_cols             | Solo usa la columna pasada [lista de strings] para hacer un marco de datos                    |
| estrujar             | Si es verdadero y solo se pasa una columna, devuelve la serie pandas                          |
| salteadores          | Omite las filas pasadas en el nuevo marco de datos                                            |
