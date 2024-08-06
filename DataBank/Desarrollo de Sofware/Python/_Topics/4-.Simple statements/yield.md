La declaracion yield se usa para definir una funcion generadora. Una funcion generadora es un tipo especial de funcion que devuelve un objeto generador que podemos iterar sobre para obtener una serie de valores.  ^4047cc

| Funciones normales            | Funciones generadoras                                                                     |
| ----------------------------- | ----------------------------------------------------------------------------------------- |
| Devuelven un valor y terminan | Pueden pausar la ejecucion y renaudarla, permitiendo producir una secuencia de resultados |

^a9460b

```python
def cuenta_regresiva(n):
    while n > 0:
        yield n
        n -= 1

for numero in cuenta_regresiva(5):
    print(numero)
```

Ahi no utilizamos return por que simplemente nos devolveria de forma que no seria comodo, yield es como una fuga de datos que si bien no se guardan, sefiltran para diferentes usos.

## Usos practivos

### Generadores infinitos
Los generadores pueden ser infinitos, lo que sería imposible con una lista regular debido a las limitaciones de memoria.
```python
def numeros_naturales():
    n = 1
    while True:
        yield n
        n += 1

numeros = numeros_naturales()
for i in range(10):
    print(next(numeros))  # Imprime los primeros 10 números naturales
```

### Corutinas
Las funciones generadoras también pueden ser utilizadas como corutinas, que son similares a los generadores pero también pueden consumir valores utilizando la declaración `yield`. Esto permite que las corutinas reciban valores del exterior de la función.
```python
def corutina():
    while True:
        valor_recibido = yield
        print(f'Valor recibido: {valor_recibido}')

c = corutina()
next(c)  # Inicializa la corutina
c.send('Hola')  # Imprime "Valor recibido: Hola"
```

### Generadores para manejo de archivos
Si estás trabajando con archivos grandes que no caben en la memoria, puedes utilizar un generador para procesar el archivo línea por línea.
```python
def leer_archivo_grande(archivo):
    with open(archivo, 'r') as f:
        for linea in f:
            yield linea

for linea in leer_archivo_grande('mi_archivo_grande.txt'):
    print(linea)  # Procesa cada línea individualmente
```