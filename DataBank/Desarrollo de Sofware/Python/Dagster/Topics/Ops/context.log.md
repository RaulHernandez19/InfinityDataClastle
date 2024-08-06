
## <font color="#b2a2c7">Concepto</font>

En dagster puedes imprimir mensajes de registro durante la ejecución de una operación utilizando el objeto `context.log`. Este objeto tiene varios métodos que corresponden a diferentes niveles de registro, como: ^08ee9d

## Ejemplos

```python
@op
def my_op(context):
    context.log.debug('Este es un mensaje de debug')
    context.log.info('Este es un mensaje de info')
    context.log.warning('Este es un mensaje de warning')
    context.log.error('Este es un mensaje de error')
```

