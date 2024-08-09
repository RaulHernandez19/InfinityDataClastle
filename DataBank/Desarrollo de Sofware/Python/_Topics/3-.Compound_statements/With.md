La declaración `with` en Python es una forma de simplificar la administración de recursos, como la apertura y cierre de archivos, la adquisición y liberación de bloqueos, entre otras tareas que normalmente requieren una estructura [[Try]]...except...finally. El uso de `with` asegura que los recursos se gestionen de manera correcta y eficiente, incluso si ocurre una excepción. ^08312b

```python
with expresión as variable:
    # Código que se ejecuta dentro del contexto
```

### Gestión de Archivos

Uno de los usos más comunes de `with` es la gestión de archivos. En lugar de abrir y cerrar archivos manualmente, `with` se encarga de cerrarlos automáticamente, incluso si ocurre un error.

```python
with open("archivo.txt", "r") as file:
    contenido = file.read()
    # No es necesario cerrar el archivo manualmente
```

### Funciones avanzadas

#### <font color="#d99694">Multiples gestores </font>
Puedes usar múltiples gestores de contexto en una sola declaración `with`. Esto es útil cuando necesitas manejar varios recursos simultáneamente.
```python
with open("archivo1.txt", "r") as file1, open("archivo2.txt", "w") as file2:
    contenido = file1.read()
    file2.write(contenido)
```

#### <font color="#d99694">Gestores de contexto personalizados</font>
Puedes crear tus propios gestores de contexto definiendo una clase con los métodos `__enter__` y `__exit__`. Esto te permite controlar cómo se inicia y termina el contexto, proporcionando una forma estructurada de manejar recursos o realizar operaciones que requieran limpieza.
```python
class Temporizador:
    def __enter__(self):
        import time
        self.inicio = time.time()
        print("Temporizador iniciado.")
        return self

    def __exit__(self, tipo_excepcion, valor_excepcion, traza):
        import time
        duracion = time.time() - self.inicio
        print(f"Temporizador detenido. Duración: {duracion:.2f} segundos.")
        # Puedes manejar excepciones aquí, si es necesario
        return False  # No suprime las excepciones

with Temporizador() as t:
    # Código cuyo tiempo quieres medir
    for i in range(1000000):
        pass
```

#### <font color="#d99694">Usar contextlib para crear gestores de contexto</font>
El módulo `contextlib` proporciona una forma sencilla de crear gestores de contexto usando el decorador `@contextmanager`. Esto es útil cuando no quieres definir una clase completa.
```python
from contextlib import contextmanager

@contextmanager
def temporizador():
    import time
    inicio = time.time()
    print("Temporizador iniciado.")
    try:
        yield
    finally:
        duracion = time.time() - inicio
        print(f"Temporizador detenido. Duración: {duracion:.2f} segundos.")

with temporizador():
    # Código cuyo tiempo quieres medir
    for i in range(1000000):
        pass
```
### Comandos de apertura
#### Modos de apertura basicos
##### 1-.Modo lectura ("r")
Abre el archivo solo para lectura. Si el archivo no existe, se lanzará una excepción `FileNotFoundError`.
```python
with open("archivo.txt", "r") as file:
    contenido = file.read()
    print(contenido)
```

##### 1-.Modo lectura ("r")
Abre el archivo para escritura. Si el archivo ya existe, su contenido se borra. Si el archivo no existe, se crea uno nuevo.
```python
with open("archivo.txt", "w") as file:
    file.write("Escribiendo nuevo contenido.")
```

#### Modos de apertura con codificacion
##### 1-.Modo de Lectura con Codificación (`"r", encoding="utf-8"`)
Abre el archivo para lectura con una codificación específica. Útil para manejar archivos de texto con diferentes codificaciones.
```python
with open("archivo.txt", "r", encoding="utf-8") as file:
    contenido = file.read()
    print(contenido)
```
##### 2-.Modo de Escritura con Codificación (`"w", encoding="utf-8"`)
Abre el archivo para escritura con una codificación específica.
```python
with open("archivo.txt", "w", encoding="utf-8") as file: file.write("Escribiendo contenido con codificación utf-8.")
```

#### Modos de apertura binario
##### 1-.Modo de Lectura Binaria (`"rb"`)
Abre el archivo en modo binario solo para lectura. No se realiza decodificación del contenido.
```python
with open("archivo.bin", "rb") as file:
    contenido = file.read()
    print(contenido)
```
##### 2-.Modo de Escritura Binaria (`"wb"`)
Abre el archivo en modo binario para escritura. Si el archivo ya existe, su contenido se borra. Si el archivo no existe, se crea uno nuevo.
```python
with open("archivo.bin", "wb") as file:
    file.write(b"\x00\x01\x02\x03")
```
##### 3-.Modo de Añadido Binario (`"ab"`)
Abre el archivo en modo binario para añadir contenido al final del archivo. Si el archivo no existe, se crea uno nuevo.
```python
with open("archivo.bin", "ab") as file:
    file.write(b"\x04\x05\x06")
```

#### Modo lectura y escritura
##### 1-.Modo de Lectura y Escritura (`"r+"`)
Abre el archivo para lectura y escritura. No borra el contenido existente y no crea el archivo si no existe.
```python
with open("archivo.txt", "r+") as file:
    contenido = file.read()
    file.seek(0)  # Volver al inicio del archivo
    file.write("Nuevo contenido.")
```
##### 2-.Modo de Lectura y Escritura Binaria (`"rb+"`)
Abre el archivo en modo binario para lectura y escritura. No borra el contenido existente y no crea el archivo si no existe.
```python
with open("archivo.bin", "rb+") as file:
    contenido = file.read()
    file.seek(0)
    file.write(b"\x07\x08\x09")
```

