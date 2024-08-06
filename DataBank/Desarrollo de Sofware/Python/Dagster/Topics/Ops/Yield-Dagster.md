## <font color="#b2a2c7">Concepto</font>

En Python, `yield` es una palabra clave que se utiliza en una función como un generador. Un generador es un tipo especial de iterador que produce valores sobre la marcha y puede pausarse y reanudarse. En el contexto de Dagster, `yield` se utiliza para producir salidas desde una operación (op). ^14d156

## <font color="#b2a2c7">Tipos</font>

Ahora, en cuanto a la diferencia entre `yield DynamicOutput` y `yield Output` en Dagster:

1. **yield DynamicOutput**: Se utiliza para producir múltiples salidas dinámicas desde una operación. Cada `DynamicOutput` producido por una operación representa un elemento en un conjunto que puede ser procesado individualmente con `map` o recogido con `collect`. [Cada  `DynamicOutput` debe tener una `mapping_key` única para distinguirlo dentro de su conjunto] <font color="#4f81bd">En tu ejemplo, está generando múltiples salidas dinámicas con el nombre “platform”, cada una con un valor y una clave de mapeo únicos.</font>
```python
yield DynamicOutput(value = canasta, mapping_key = str(i), output_name = "canasta")
```

2. **yield Output**: Se utiliza para producir una única salida desde una operación. Por defecto, todas las operaciones tienen una única salida llamada “result”. [Cuando tienes una salida, puedes devolver el valor de la salida directamente](https://docs.dagster.io/concepts/ops-jobs-graphs/ops)[2](https://docs.dagster.io/concepts/ops-jobs-graphs/ops). <font color="#4f81bd">En tu ejemplo, está generando una única salida con el nombre “testers” y un valor específico.</font>
```python
yield Output(value=testers, output_name="frutas")
```

## Referencias

(https://docs.dagster.io/_apidocs/dynamic)[1](https://docs.dagster.io/_apidocs/dynamic).