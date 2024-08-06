Se utiliza para lanzar excepciones, especificando el tipo y un mensaje. ^d472e5

```python
raise ValueError('Un valor no válido')
```

### Re-lanzamiento de excepciones
Si usas raise sin argumentos dentro de un excep, volvera a lanzar la excepcion que se esta manejando actualmente.

```python
try:
    1 / 0  # Lanza ZeroDivisionError
except ZeroDivisionError:
    print('Error de división por cero!')
    raise  # Vuelve a lanzar ZeroDivisionError
```

### Excepciones con trazas personalizadas
Se puede asociar una traza personalizada a una excepcion usando el metodo with_traceback()

```python
try:
    raise ValueError('Un valor no válido').with_traceback(None)
except ValueError as e:
    print(e)  # Imprime "Un valor no válido"
```

## Encadena excepciones
Se puede encadenar una excepcion a otra con raise...from

```python
try:
    {}['clave_inexistente']  # Lanza KeyError
except KeyError as e:
    raise ValueError('Clave no encontrada en el diccionario') from e
```

# Ejemplos utiles

## Validar datos de entrada
```python
def dividir(numerador, denominador):
    if denominador == 0:
        raise ValueError('El denominador no puede ser cero')
    return numerador / denominador

try:
    resultado = dividir(5, 0)
except ValueError as e:
    print(f'Error: {e}')  # Imprime "Error: El denominador no puede ser cero"
```

## Manejo de errores en la apertura de archivos

```python
def leer_archivo(nombre_archivo):
    try:
        with open(nombre_archivo, 'r') as archivo:
            return archivo.read()
    except FileNotFoundError:
        raise ValueError(f'El archivo {nombre_archivo} no se encontró')

try:
    contenido = leer_archivo('archivo_inexistente.txt')
except ValueError as e:
    print(f'Error: {e}')  # Imprime "Error: El archivo archivo_inexistente.txt no se encontró"
```