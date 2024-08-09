El bloque `try` contiene el código que quieres "proteger". Si en este bloque ocurre una excepción, la ejecución se detiene inmediatamente y se transfiere el control al bloque `except` correspondiente.

```python
try:
    # Código que puede generar una excepción
except NombreDeLaExcepcion as e:
    # Código que se ejecuta si ocurre la excepción especificada
else:
    # Código que se ejecuta si NO ocurre ninguna excepción
finally:
    # Código que se ejecuta SIEMPRE, haya o no excepción
```

###### finally 
El bloque `finally` se ejecuta siempre, independientemente de si ocurre o no una excepción. Se utiliza generalmente para realizar tareas de limpieza, como cerrar archivos o liberar recursos.
```python
try:
    file = open("archivo.txt", "r")
    contenido = file.read()
except FileNotFoundError:
    print("Error: Archivo no encontrado.")
finally:
    file.close()  # Se cierra el archivo aunque ocurra un error
```

#### Ejemplo practico

```python
try:
    file = open("archivo.txt", "r")
    contenido = file.read()
    numero = int(contenido)
except FileNotFoundError:
    print("Error: El archivo no existe.")
except ValueError:
    print("Error: El contenido no es un número válido.")
else:
    print(f"El número en el archivo es: {numero}")
finally:
    print("Cerrando el archivo.")
    file.close()
```