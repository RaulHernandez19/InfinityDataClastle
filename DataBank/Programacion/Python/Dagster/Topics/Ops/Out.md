
Out
```python

@op(out={Values})

```

| Values                 |                             |                                                                                                                                                                                                                                                                                                                                                                                                         |
| ---------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Out                    | is_required=(True\|\|False) | Es una variante de `DynamicOut` que se utiliza para una salida que alterará dinámicamente el gráfico en tiempo de ejecución                                                                                                                                                                                                                                                                             |
| required_resource_keys | {"values"}                  | En la ingeniería de datos, los recursos son los servicios externos, herramientas y almacenamiento que utilizas para hacer tu trabajo. Los `required_resource_keys` son típicamente un conjunto de valores de configuración, que se utilizan para especificar cosas como identificadores de cuenta, claves API, o nombres de bases de datos cuando se interactúa con una herramienta o servicio externo] |
| DynamicOut             | is_required=(True\|\|False) | Es una variante de `Out` para una salida que alterará dinámicamente el gráfico en tiempo de ejecución. Cuando se usa en una función de composición como `@graph`, las salidas dinámicas deben usarse con `map` (clonar operaciones aguas abajo para cada `DynamicOut` separado) o `collect` (reunir todos los `DynamicOut` en una lista                                                                 |
|                        |                             |                                                                                                                                                                                                                                                                                                                                                                                                         |

Fuentes:
(https://docs.dagster.io/_apidocs/dynamic)[1](https://docs.dagster.io/_apidocs/dynamic).
(https://docs.dagster.io/concepts/resources)[2](https://docs.dagster.io/concepts/resources).
(https://docs.dagster.io/_apidocs/dynamic)[1](https://docs.dagster.io/_apidocs/dynamic).