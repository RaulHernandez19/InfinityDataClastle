

>Es una herramienta la cual nos ayuda a tener un mejor monitoreo del codigo y orquestacion de datos segmentandolo.

```bash
pip install dagster
dagster project scaffold --name my-dagster-project
cd my-dagster-project
pip install -e '.[dev]'
```
###  [[Install and running]] 
### [[Flujo_Dagster.canvas|Flujo_Dagster]]
# 🏧 <font color="#b2a2c7">Automation</font>

- ### [[Schedules]]

- ### Sensors 

# 🔎 <font color="#c3d69b">Concepts</font>

- ### 💼 [[Jobs]]

- ### 🥢

- ### 📰 [[Resources]]

- ### ⚙️[[Config]]

- ### 📊 [[Graph]]

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
|                      | An output of an op. Defined on the `out` argument to the `@op`decorator.                                                                                                         |
| `OpExecutionContext` | An object exposing Dagster system APIs for resource access, logging, and more. Can be injected into an op by specifying `context` as the first argument of the compute function. |
| `OpDefinition`       | Class for ops. You will rarely want to instantiate this class directly. Instead, you should use the                                                                              |
|                      |                                                                                                                                                                                  |
|                      |                                                                                                                                                                                  |
[[Out]]

>[!PRE-NOTES]
>
Defs: 
ops: Seria definir una funcion que tiene una salida clara con un def
(Cada cosa de abajo puede ir en su propia carpeta )
Jobs: Descipcion, tags y resourse_defs  
Schedules: Tarea rutinaria, 
Op Puede tener muchos Jobs y dentro de los jobs multiple Schedules
Se tiene Config  para poder modificar desde dagster cosas claves

#languageComplement 