>Estos sirve para que cada [[Ops]] correspondiente tenga configuraciones a la hora de ejecutarlo.
#### Format: 

	1.Primero se tiene la (Config) que se exporta de dagster

```python
class nombre_class(config):
	variable: tipo de dato = "Opciones de configuracion"
```

	2.Dentro de un [[Ops]] se aplica:

```python
def ejemplo (config: nombre_class)
	config_data = config.model_dump()
```

