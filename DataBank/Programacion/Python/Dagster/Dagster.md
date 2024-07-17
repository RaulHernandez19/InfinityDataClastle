

>Es una herramienta la cual nos ayuda a tener un mejor monitoreo del codigo y orquestacion de datos segmentandolo.

```bash
pip install dagster
dagster project scaffold --name my-dagster-project
cd my-dagster-project
pip install -e '.[dev]'
```
###  [[Install and running]] 
## Dagster Flow ![[Dagster_Flow.excalidraw|500]]
# 🏧 <font color="#b2a2c7">Automatic</font>

- ### [[Schedules]]

- ### Sensors 

# 🔎 <font color="#c3d69b">Concepts</font>

- ### 💼 [[Jobs]]

- ### 🥢[[Ops]]

- ### 📰 [[Resources]]

- ### ⚙️[[Config]]

- ### 📊 [[Graph]]


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