**Poetry** es una herramienta para la gestión de dependencias y el empaquetado en Python. Te permite declarar las bibliotecas de las que depende tu proyecto y las administrará (instalará/actualizará) por ti. Poetry también te ayuda a empaquetar tu proyecto para su distribución.

### Comandos 

- `pip install poetry`: Installa el paquete necesario para usar poetry.

- `poetry init`: Crea el `pyproject.toml`.

- `poetry new nombre_del_proyecto`: Este comando crea un nuevo proyecto de Poetry con el nombre especificado. Genera una estructura de directorios y un archivo `pyproject.toml` predeterminado.
    
- `poetry add nombre_del_paquete`: Este comando agrega una nueva dependencia a tu proyecto. Poetry buscará el paquete especificado, lo instalará y lo agregará a la lista de dependencias en tu archivo `pyproject.toml`.
    
- `poetry remove nombre_del_paquete`: Este comando elimina una dependencia de tu proyecto. Poetry eliminará el paquete especificado de tu entorno virtual y también lo eliminará de la lista de dependencias en tu archivo `pyproject.toml`.
    
- `poetry install`: Este comando instala todas las dependencias de tu proyecto (especificadas en tu archivo `pyproject.toml`) en tu entorno virtual.
    
- `poetry update`: Este comando actualiza las dependencias de tu proyecto a sus últimas versiones.
    
- `poetry build`: Este comando empaqueta tu proyecto para su distribución. Genera archivos de distribución que puedes subir a PyPI.
    
- `poetry publish`: Este comando publica tu proyecto en PyPI.
    
- `poetry shell`: Este comando inicia un nuevo shell interactivo con el entorno virtual activado.
    
- `poetry run comando`: Este comando ejecuta el comando especificado en el entorno virtual de tu proyecto.

#Ejemplo: