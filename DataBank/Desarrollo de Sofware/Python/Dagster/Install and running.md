
# 1. ![[Virtual enviroment]]
-->Make a folder with the name: "dagster_home

# 2. Install poetry

```bash
pip install poetry
```

# 3.Install dependencies with poetry

```bash
poetry install
```

## 3.5 Or install the dependencies

```
python = "^3.10"
pyarrow = "^15.0.0"
numpy = "^1.26.4"
pandas = "^2.2.0"
pyodbc = "^5.1.0"
requests = "^2.31.0"
dagster = "^1.6.5"
dagster-webserver = "^1.6.5"
Requests = "^2.31.0"
paramiko = "^3.4.0"
fabric = "^2.4.0"
```

Importante asignarle 
```
[tool.dagster]
module_name = "dagster_Monitoring"
```
# 4.Dagster Home declaration
```bash
$env:DAGSTER_HOME= "C:path\to\dagster_home"
#Or set DAGSTER_HOME=path
```

# 5.Run dagster
```bash
dagster dev
```