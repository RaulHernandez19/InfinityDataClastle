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

# 💠Tips

1. Tener un `__init__`.py para poder correr el dagster de forma mas sencilla y prestablecer los jobs y mas estructuras 
```python
from dagster import (
    Definitions,
    ScheduleDefinition,
)

from .jobs.archivosJobs import (
    nombreDelJob
)

testerschedule = ScheduleDefinition(
    job=nombreDelJob,
    cron_schedule='0 * * * *'
)

defs = Definitions(
    jobs = [
        nombreDelJob                                    
    ],
    schedules = [
        tester_monitoring_schedule
    ]
)
```

#languageComplement 