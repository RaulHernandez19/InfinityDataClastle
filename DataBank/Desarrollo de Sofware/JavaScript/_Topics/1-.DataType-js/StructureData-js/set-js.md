Estructura de datos de valores unicos. Siendo utilizado comunmente para asegurarse de que una coleccion de objetos no contenga duplicados, asi como en la eliminacion de duplicados de un array o gestion de datos unicos. ^eef260

##### Sintaxis
```javascript
let miSet = new Set();
miSet.add(1);
miSet.add(2);
miSet.add(2); // No se añadirá porque ya existe
miSet.add(3);

console.log(miSet); // Set { 1, 2, 3 }
```

## <font color="#fdeada">Metodos</font>

```javascript
miSet.add(4); //ADD
console.log(miSet); // Set { 1, 2, 3, 4 }

miSet.delete(2); //DELETE
console.log(miSet); // Set { 1, 3, 4 }

console.log(miSet.has(3)); // true !-//HAS
console.log(miSet.has(2)); // false

miSet.clear(); //CLEAR
console.log(miSet); // Set {}

miSet.add(1); 
miSet.add(2);
console.log(miSet.size); // 2 !-//SIZE
```

## Ejemplos
```javascript
let frutas = new Set();
frutas.add("manzana");
frutas.add("banana");
frutas.add("pera");

console.log(frutas.has("manzana")); // true
console.log(frutas.size); // 3

frutas.delete("banana");
console.log(frutas); // Set { "manzana", "pera" }

frutas.clear();
console.log(frutas); // Set {}
```