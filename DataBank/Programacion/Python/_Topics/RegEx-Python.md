Las expresiones regulares, también conocidas como **RegEx**, son una herramienta esencial en el conjunto de herramientas del programador de PythonProporcionan una manera poderosa de coincidir patrones dentro del texto, permitiendo a los desarrolladores buscar, manipular e incluso validar datos de manera eficiente

```python
impor re #import necesario
```

### <font color="#8db3e2">Tipos</font>

#### <font color="#d99694">1-re.search</font>

`(pattern, string)` Este método busca el patrón en toda la cadena de texto. Si el patrón se encuentra, devuelve un objeto de coincidencia, de lo contrario devuelve `None`.
 ```python
texto = "Hola Mundo"
resultado = re.search("Mundo", texto)
print(resultado)
```
>En este caso, `resultado` será un objeto de coincidencia ya que “Mundo” se encuentra en la cadena de texto “Hola Mundo”.
#### <font color="#d99694">2-re.match</font>

`(pattern, string`) Este método busca el patrón solo al comienzo de la cadena de texto. Si el patrón se encuentra al comienzo de la cadena, devuelve un objeto de coincidencia, de lo contrario devuelve `None`.
```python
texto = "Hola Mundo"
resultado = re.match("Hola", texto)
print(resultado)
```
>En este caso, `resultado` será un objeto de coincidencia ya que “Hola” se encuentra al comienzo de la cadena de texto “Hola Mundo”.
#### <font color="#d99694">3-re.findall</font>

`(pattern, string`) Este método devuelve todas las coincidencias del patrón en la cadena de texto como una lista de cadenas. La cadena se escanea de izquierda a derecha y las coincidencias se devuelven en el orden en que se encuentran.
```python
texto = "Hola Mundo, Mundo"
resultado = re.findall("Mundo", texto)
print(resultado)
```
#### <font color="#d99694">4-re.split</font>

`(pattern, string, maxsplit=0)` Este método divide la cadena por las ocurrencias del patrón especificado.
```python
texto = "Hola Mundo, Mundo"
resultado = re.split("\s", texto)
print(resultado)
```
>En este caso, `resultado` será `['Hola', 'Mundo,', 'Mundo']` ya que se divide la cadena de texto “Hola Mundo, Mundo” por los espacios.
#### <font color="#d99694">5-re.sub</font>
`(pattern, repl, string, count=0)` Este método reemplaza todas las ocurrencias del patrón en la cadena por `repl`, sustituyendo todas las ocurrencias a menos que `count` sea un número no cero.
```python
import re
texto = "Hola Mundo, Mundo"
resultado = re.sub("Mundo", "Python", texto)
print(resultado)
```
>En este caso, `resultado` será `"Hola Python, Python"` ya que se reemplaza “Mundo” por “Python” en la cadena de texto “Hola Mundo, Mundo”.
 
#### <font color="#d99694">6-re.compile</font>
`(pattern) `Este método compila un patrón de expresión regular en un objeto de expresión regular, que puede usarse para hacer coincidir con `match()`, `search()` y otros métodos.
```python
import re
patron = re.compile("Mundo")
texto = "Hola Mundo, Mundo"
resultado = patron.findall(texto)
print(resultado)
```
>En este caso, `resultado` será `['Mundo', 'Mundo']` ya que “Mundo” se encuentra dos veces en la cadena de texto “Hola Mundo, Mundo”.

### Ejemplos practicos:

**Ejemplo -1: Saber si en un String esta una lista de palabras**
```python
regexList = r".*(" + '|'.join(list) + ").*"
re.search(regexList, "string")
```

**Ejemplo -0 Saber si en un String se encuentra alguna de las opciones en su final.
```python

regex: str = r".*\.(option2|option3|option1)$"
CompileRegex=re.compile(configPattern)
pattern.match(file_entry.path)
```

**Ejemplo 1: Encontrar una dirección de correo electrónico en un texto**
```python
text = "For more information, contact us at  info@example.com."
match = re.findall(r'\\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Z|a-z]{2,}\\b', text) 
print("Email Address Found:", match)
```

**Ejemplo 2: Validar un número de teléfono**
```python
def validate_phone_number(number):
    if re.match(r'^\\+?1?\\d{9,15}$', number):
        return True
    return False 

number = "+1234567890"
print("Is Valid Phone Number:", validate_phone_number(number))
```
