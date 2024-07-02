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