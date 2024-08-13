Los objetos son colecciones de pares clave-valor, donde cada clave (también llamada propiedad) está asociada a un valor.

```javascript
let frutas = {
  manzana: "rojo",
  banana: "amarillo",
  pera: "verde"
};

console.log(frutas); // { manzana: "rojo", banana: "amarillo", pera: "verde" }
```
En vez de index automatico como en [[array-js]], aqui cada elemento tiene una `key` y aqui si se puede tener diferentes tipos de datos a comparacion del array que solo tiene un tipo de dato.

## Acceder a una porpiedad

```js
const persona={
	nombre: "David",
	edad: 24,
	comidaFav: "Mojonles"
}

let edad = persona.edad;

//OR

let v="edad"
persona[v]=24
```
## Editar propiedad
```js
persona.edad=100;
```
## Agregar nueva propiedad
```js
perosna.deporteFav="natacion"
```
## Eliminar propiedad
```js
delete persona.comidaFav;
```
## Recorrer un objeto
```js
for (let key in persona){
	console.log(key,persona[key]);
}
```

## This
```js
let user = {
  name: "John",
  age: 30,
  sayHi() {
    // "this" is the "current object"
    alert(this.name);
  }
};
user.sayHi(); // John
```

## New
Una **Function Constructor** es una función regular que se utiliza para crear objetos. La convención es nombrarla con la primera letra en mayúscula y ejecutarla con el operador `new`.
Cuando usas `new` con una función, realiza los siguientes pasos:

1. **Crea un nuevo objeto vacío.**
2. **Asigna ese objeto a `this` dentro de la función.**
3. **Ejecuta el código de la función, modificando `this`.**
4. **Devuelve el objeto `this` automáticamente.**
```javascript
function User(name) {
  this.name = name;
  this.isAdmin = false;
}

let user = new User("Jack");

console.log(user.name); // Jack
console.log(user.isAdmin); // false
```
## ![[for-js#Bucle `for...in`]]
Importante conocer: [[Object+Array]]