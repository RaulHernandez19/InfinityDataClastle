Las `labels` pueden ser una sola etiqueta o etiquetas de índice o de columna en forma de lista para ser eliminadas.

El `axis` especifica si las etiquetas se eliminan del índice/fila (`0` o `index`) o de la columna (`1` o `columns`).

El `index` y las `columns` son la alternativa para especificar el eje. `drop(labels, axis=0)` es igual a `drop(index=labels)`, mientras que `drop(labels, axis=1)` es igual a `drop(column=labels)`.

`inplace` especifica que el DataFrame se modifica en el lugar si `inplace = True`, de lo contrario, devuelve el nuevo DataFrame con el DataFrame original sin modificar.

![[Pasted image 20240625145006.png]]