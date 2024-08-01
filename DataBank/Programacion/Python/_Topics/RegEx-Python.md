Las expresiones regulares, también conocidas como **RegEx**, son una herramienta esencial en el conjunto de herramientas del programador de PythonProporcionan una manera poderosa de coincidir patrones dentro del texto, permitiendo a los desarrolladores buscar, manipular e incluso validar datos de manera eficiente

Ejemplos utiles:
```python
regexList = r".*(" + '|'.join(list) + ").*"
```

```python
regez: str = r".*\.(option2|option3|option1)$"
```

**Ejemplo 1: Encontrar una dirección de correo electrónico en un texto**
```python
import re 

text = "For more information, contact us at  info@example.com."
match = re.findall(r'\\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Z|a-z]{2,}\\b', text) 
print("Email Address Found:", match)
```

**Ejemplo 2: Validar un número de teléfono**
```python
import re 

def validate_phone_number(number):
    if re.match(r'^\\+?1?\\d{9,15}$', number):
        return True
    return False 

number = "+1234567890"
print("Is Valid Phone Number:", validate_phone_number(number))
```