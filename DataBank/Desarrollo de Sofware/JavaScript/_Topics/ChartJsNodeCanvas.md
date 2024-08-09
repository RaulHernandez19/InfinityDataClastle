>**ChartjsNodeCanvas** es un renderizador de gráficos para Node.js que utiliza la biblioteca Chart.js y el API de Canvas. Permite generar gráficos en el servidor sin necesidad de un entorno de navegador.
```js
npm install chartjs-node-canvas chart.js
```
# Values

1. **type**: Es el tipo de gráfico. En este caso, es ‘bar’ para un gráfico de barras.
    
2. **data**: Contiene los datos del gráfico.
    
    - **labels**: Son las etiquetas para los puntos de datos. En este caso, son los nombres de los colores.
    - **datasets**: Es un arreglo de objetos que representan los conjuntos de datos.
        - **label**: Es la etiqueta para el conjunto de datos.
        - **data**: Son los datos numéricos a graficar.
        - **backgroundColor**: Es el color de fondo de las barras en el gráfico.
        - **borderColor**: Es el color del borde de las barras en el gráfico.
        - **borderWidth**: Es el ancho del borde de las barras en el gráfico.
3. **options**: Contiene las opciones de configuración del gráfico. En este caso, está vacío.
    
4. **plugins**: Contiene los plugins a utilizar en el gráfico.
    
    - **id**: Es el identificador del plugin.
    - **beforeDraw**: Es una función que se ejecuta antes de dibujar el gráfico.

Además de estos, hay otros valores y sub-valores que se pueden tener en la configuración del gráfico:

- **responsive**: Si es `true`, el gráfico se redimensionará cuando cambie el tamaño de la ventana.
- **maintainAspectRatio**: Si es `false`, el gráfico no mantendrá el aspecto original cuando cambie el tamaño de la ventana.
- **title**: Permite agregar un título al gráfico.
- **legend**: Permite configurar la leyenda del gráfico.
- **tooltips**: Permite configurar los tooltips que aparecen cuando se pasa el cursor sobre un punto de datos.
- **animation**: Permite configurar las animaciones del gráfico.

# Explicacion ejemplo

## 1-.Imports

```js
import { ChartJSNodeCanvas, ChartCallback } from './';
import { ChartConfiguration } from 'chart.js';
import { promises as fs } from 'fs';
```
### 2-.Main function

```js
async function main(): Promise<void> {
```

### 3-.Chart configuration 

```js
const width = 400;
const height = 400;
const configuration: ChartConfiguration = {
    type: 'bar',
    data: {
        labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
        datasets: [{
            label: '# of Votes',
            data: [12, 19, 3, 5, 2, 3],
            backgroundColor: [
                'rgba(255, 99, 132, 0.2)',
                'rgba(54, 162, 235, 0.2)',
                'rgba(255, 206, 86, 0.2)',
                'rgba(75, 192, 192, 0.2)',
                'rgba(153, 102, 255, 0.2)',
                'rgba(255, 159, 64, 0.2)'
            ],
            borderColor: [
                'rgba(255,99,132,1)',
                'rgba(54, 162, 235, 1)',
                'rgba(255, 206, 86, 1)',
                'rgba(75, 192, 192, 1)',
                'rgba(153, 102, 255, 1)',
                'rgba(255, 159, 64, 1)'
            ],
            borderWidth: 1
        }]
    },
    options: {
    },
    plugins: [{
        id: 'background-colour',
        beforeDraw: (chart) => {
            const ctx = chart.ctx;
            ctx.save();
            ctx.fillStyle = 'white';
            ctx.fillRect(0, 0, width, height);
            ctx.restore();
        }
    }]
};
```

### 4-.Chart callback

```js
const chartCallback: ChartCallback = (ChartJS) => {
    ChartJS.defaults.responsive = true;
    ChartJS.defaults.maintainAspectRatio = false;
};
```

### 5-.Creating the chart

```javascript
const chartJSNodeCanvas = new ChartJSNodeCanvas({ width, height, chartCallback });
const buffer = await chartJSNodeCanvas.renderToBuffer(configuration);
```

### Save the chart

```javascript
await fs.writeFile('./example.png', buffer, 'base64');
```

7-.Run the main funtion(???
```js
main();
```


[Documentation](https://github.com/SeanSobey/ChartjsNodeCanvas)