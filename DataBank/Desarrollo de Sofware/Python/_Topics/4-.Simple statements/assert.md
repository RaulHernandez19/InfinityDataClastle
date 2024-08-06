## Que es?

Herramienta de purifiacion que permite verificar si una condicion es verdadera. Si es verdadera el programa continua ejecutandose, peor si no, se lanzara una excepcion `AssertionError`. ^f3fdd4

## Forma simple
```python
# Ejemplo
x = 5
assert x > 0  # No pasa nada porque x es mayor que 0
assert x < 0  # Se lanza una excepción AssertionError porque x no es menor que 0
```
## Forma extendida
```python
# Ejemplo
x = 5
assert x > 0, "x debe ser mayor que 0"  # No pasa nada porque x es mayor que 0
assert x < 0, "x no puede ser menor que 0"  # Se lanza una excepción AssertionError con el mensaje "x no puede ser menor que 0"
```