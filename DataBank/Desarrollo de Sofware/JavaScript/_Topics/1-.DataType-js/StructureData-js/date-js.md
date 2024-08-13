## <font color="#fdeada">Creacion de un date</font>

##### 1-.Fecha y hora actuales
```javascript
let fechaActual = new Date();
console.log(fechaActual);
```
##### 2-. Fecha especifica (aa,MM,dd,hh,mm,ss,ms)
```javascript
let fechaEspecifica = new Date(2024, 7, 13, 15, 42, 30, 0); // 13 de agosto de 2024, 15:42:30
console.log(fechaEspecifica);
```
##### 3-.Transformar cadena
```javascript
let fechaCadena = new Date("August 13, 2024 15:42:30");
console.log(fechaCadena);
```
##### 4-.Fecha a partir de milisegundos desde 1 enero de 1970 (Epoch)
```javascript
let fechaMilisegundos = new Date(1628877750000);
console.log(fechaMilisegundos);
```

## <font color="#fdeada">Formatos</font>

##### 1-.ISO 8601
```javascript
let fechaISO = new Date("2024-08-13T15:42:30Z");
console.log(fechaISO);
```
##### 2-.Cadena corta
```javascript
let fechaCorta = new Date("08/13/2024");
console.log(fechaCorta);
```
##### 3-.Cadena de fecha larga
```javascript
let fechaLarga = new Date("August 13, 2024 15:42:30");
console.log(fechaLarga);
```

## <font color="#fdeada">Metodos</font>

##### Obtener componentes de la fecha
```javascript
let fecha = new Date();
console.log(fecha.getFullYear()); // Año
console.log(fecha.getMonth()); // Mes (0-11)
console.log(fecha.getDate()); // Día del mes (1-31)
console.log(fecha.getHours()); // Hora (0-23)
console.log(fecha.getMinutes()); // Minutos (0-59)
console.log(fecha.getSeconds()); // Segundos (0-59)
```

##### Establecer componentes de fecha
```javascript
let fecha = new Date();
fecha.setFullYear(2025);
fecha.setMonth(11); // Diciembre
fecha.setDate(25);
console.log(fecha);
```

##### Convertir a cadena
```javascript
let fecha = new Date();
console.log(fecha.toISOString()); // Formato ISO
console.log(fecha.toDateString()); // Fecha en formato legible
console.log(fecha.t
```


