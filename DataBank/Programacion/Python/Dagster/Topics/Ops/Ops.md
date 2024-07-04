Una `Op` es la unidad central de cálculo en Dagster.Una operación individual debería realizar tareas relativamente simples, como derivar un conjunto de datos a partir de otros conjuntos de datos, ejecutar una consulta de base de datos, iniciar un trabajo Spark en un clúster remoto, consultar una API y almacenar el resultado en un almacén de datos, enviar un correo electrónico o un mensaje de Slack

```python
from dagster import op
   
@op
def get_file_sizes():
# Aquí va la lógica de la operación
```



| Name                 | Description                                                                                                                                                                      |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `@op`                | A decorator used to define ops. Returns an `OpDefinition`. The decorated function is called the "compute function".                                                              |
| `In`                 | An input to an op. Defined on the `ins` argument to the `@op` decorator.                                                                                                         |
| [[Out]]              | An output of an op. Defined on the `out` argument to the `@op`decorator.                                                                                                         |
| `OpExecutionContext` | An object exposing Dagster system APIs for resource access, logging, and more. Can be injected into an op by specifying `context` as the first argument of the compute function. |
| `OpDefinition`       | Class for ops. You will rarely want to instantiate this class directly. Instead, you should use the                                                                              |

