### Funciones

#### basicas

1. **<font color="#fdeada">length</font>**
-  **Descripción**: Devuelve la longitud de la cadena.
-  **Sintaxis**: `string.length`
3. **<font color="#fdeada">toUpperCase()</font>**
- **Descripción**: Convierte todos los caracteres de la cadena a mayúsculas.
- **Sintaxis**: `string.toUpperCase()`
3. **<font color="#fdeada">toLowerCase()</font>**
- **Descripción**: Convierte todos los caracteres de la cadena a minúsculas.
- **Sintaxis**: `string.toLowerCase()`
4. <font color="#fdeada">charAt()</font>
- **Descripción**: Devuelve el carácter en el índice especificado.
- **Sintaxis**: `string.charAt(index)`
5. <font color="#fdeada">includes()</font>
- **Descripción**: Determina si una cadena contiene otra cadena.
- **Sintaxis**: `string.includes(substring)`
6. <font color="#fdeada">indexOf()</font>
- **Descripción**: Devuelve el índice de la primera aparición de un valor especificado en una cadena., tambien existe el <font color="#fdeada">lastIndexOf()</font> que es lo contrario.
- **Sintaxis**: `string.indexOf(searchValue)`
7. <font color="#fdeada">substring()</font>
- **Descripción**: Devuelve una parte de la cadena entre dos índices especificados.
- **Sintaxis**: `string.substring(startIndex, endIndex)`
8. <font color="#fdeada">split()</font>
- **Descripción**: Divide una cadena en un array de subcadenas, puede usar [[Regex]].
- **Sintaxis**: `string.split(separator)`

#### Avanzadas
##### <font color="#d99694">Slice()</font>
```js
let text = "Hello world!";
let result = text.slice(0, 5);
//Hello
```
#### <font color="#d99694">replace()</font>
```javascript
let texto = "Hola mundo";
let nuevoTexto = texto.replace("mundo", "JavaScript");
console.log(nuevoTexto); // "Hola JavaScript"
```
#### <font color="#d99694">match()</font>
Busca una cadena usando una expresión regular y devuelve las coincidencias usando un [[Regex]]
```javascript
let texto = "El sol brilla en el cielo";
let coincidencias = texto.match(/el/gi);
console.log(coincidencias); // ["El", "el"]
```
#### <font color="#d99694">trim()</font>
Elimina los espacios en blanco al inico y final de la cadena.
```javascript
let texto = "   Hola mundo   ";
let textoSinEspacios = texto.trim();
console.log(textoSinEspacios); // "Hola mundo"
```

#### <font color="#d99694">contact()</font>
```javascript
let saludo = "Hola";
let nombre = "Mundo";
let mensaje = saludo.concat(" ", nombre);
console.log(mensaje); // "Hola Mundo"
```

### Ejemplos avanzados
```javascript
let texto = "JavaScript es genial. JavaScript es divertido. Me encanta JavaScript.";

let palabrasUnicas = texto
  .toLowerCase() // Convertir todo a minúsculas
  .split(/[\s,.]+/) // Dividir en palabras usando espacios, comas y puntos como separadores
  .filter((valor, indice, self) => self.indexOf(valor) === indice) // Filtrar palabras únicas
  .sort(); // Ordenar alfabéticamente

console.log(palabrasUnicas); // ["", "a", "divertido", "encanta", "es", "genial", "javascript", "me"]
```