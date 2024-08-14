 Define qué propiedades y métodos tendrán los objetos creados a partir de ella.
```js
class Rectangle {
  // cuerpo de la clase
}
```
### <font color="#d99694">Constructor</font>
Es un método especial que se utiliza para crear e inicializar un objeto creado a partir de una clase. Se llama automáticamente cuando se crea un objeto a partir de una clase.
```javascript
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
```
### <font color="#d99694">init()</font>
convención comúnmente utilizada para nombrar métodos que inicializan objetos, módulos o componentes. La idea detrás de `init()` es preparar o configurar algo antes de su uso.
- Configurar valores iniciales.
- Establecer conexiones.
- Preparar el estado interno de un objeto o componente.
- Ejecutar cualquier configuración necesaria antes de que el objeto o componente esté listo para su uso.
```javascript
const myModule = (function() {
  let privateVar = 0;

  function init() {
    privateVar = 42;
    console.log("Módulo inicializado con privateVar =", privateVar);
  }

  function getPrivateVar() {
    return privateVar;
  }

  return {
    init: init,
    getPrivateVar: getPrivateVar
  };
})();

myModule.init(); // Módulo inicializado con privateVar = 42
console.log(myModule.getPrivateVar()); // 42
```
### <font color="#d99694">Metodos de clase</font> 
```javascript
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }

  // Este es un método para calcular el área del rectángulo
  calculateArea() {
    return this.height * this.width;
  }

  // Este es un método para calcular el perímetro del rectángulo
  calculatePerimeter() {
    return 2 * (this.height + this.width);
  }
}

let myRectangle = new Rectangle(5, 10);
console.log(myRectangle.calculateArea());  // Imprime 50
console.log(myRectangle.calculatePerimeter());  // Imprime 30
```

### <font color="#d99694">Clases (ES6)</font>
```javascript
class User {
  constructor(name) {
    this.name = name;
    this.isAdmin = false;
  }
}

let user = new User("Jack");

console.log(user.name); // Jack
```

### <font color="#d99694">Class Inheritance</font>
La herencia de clases permite que una clase (subclase) herede propiedades y métodos de otra clase (superclase). En JavaScript, esto se logra utilizando las palabras clave `extends` y `super`.
```javascript
class Animal {
  constructor(nombre) {
    this.nombre = nombre;
  }
  hablar() {
    console.log(`${this.nombre} hace un ruido.`);
  }
}
class Perro extends Animal {
  constructor(nombre, raza) {
    super(nombre); // Llama al constructor de la superclase
    this.raza = raza;
  }
  hablar() { //Se sobreescribe el metodo hablar
    console.log(`${this.nombre} ladra.`);
  }
}
let miPerro = new Perro("Rex", "Labrador");
miPerro.hablar(); // Rex ladra.
```

####  Inheritance and static methods
Static methods can also be inherited and overwritten.
```javascript
class Animal {
  static info() {
    console.log("Los animales son seres vivos.");
  }
}

class Perro extends Animal {
  static info() {
    super.info(); // Llama al método estático de la superclase
    console.log("Los perros son una especie de animales.");
  }
}

Perro.info();
// Salida:
// Los animales son seres vivos.
// Los perros son una especie de animales.
```

#### Herencia multiple (Mixin)
Para poder hacer herencia multiple se necesita mixins para combinar multiples comportamientos.
```javascript
let Volador = {
  volar() {
    console.log(`${this.nombre} está volando.`);
  }
};

let Nadador = {
  nadar() {
    console.log(`${this.nombre} está nadando.`);
  }
};

class Animal {
  constructor(nombre) {
    this.nombre = nombre;
  }
}

class Pato extends Animal {
  constructor(nombre) {
    super(nombre);
  }
}

Object.assign(Pato.prototype, Volador, Nadador);

let miPato = new Pato("Donald");
miPato.volar(); // Donald está volando.
miPato.nadar(); // Donald está nadando.
```

#### Encaptulacion y proteccion de datos
En ES6, puedes usar símbolos o convenciones de nomenclatura para encapsular y proteger datos, aunque no hay una verdadera privacidad de datos hasta ES2022 con campos privado.
```javascript
class Animal {
  #nombre; // Campo privado

  constructor(nombre) {
    this.#nombre = nombre;
  }

  getNombre() {
    return this.#nombre;
  }
}

let miAnimal = new Animal("Simba");
console.log(miAnimal.getNombre()); // Simba
console.log(miAnimal.#nombre); // Error: campo privado
```

#### Polimorfism
Este concepto permite que una subclase sobreescria metodos de la superclase para proporcionar una implementacion especifica.
```javascript
class Animal {
  hablar() {
    console.log("El animal hace un ruido.");
  }
}

class Perro extends Animal {
  hablar() {
    console.log("El perro ladra.");
  }
}

class Gato extends Animal {
  hablar() {
    console.log("El gato maúlla.");
  }
}

let animales = [new Perro(), new Gato()];

animales.forEach(animal => animal.hablar());
// Salida:
// El perro ladra.
// El gato maúlla.
```

### Privacity in Class
#### <font color="#fdeada">Público</font>
Para propiedades y métodos que deben ser accesibles desde cualquier lugar.
- **Accesible desde cualquier lugar.**
- **Ejemplo:** Todos los métodos y propiedades que hemos usado hasta ahora en nuestras clases.
#### <font color="#fdeada">Privado</font>
Para propiedades y métodos que deben ser completamente encapsulados dentro de la clase.
- **Accesible solo desde dentro de la clase.**
- **Ejemplo:** Campos privados en ES2022 usando `#`.
Usamos `#` para definir propiedades privadas.
```javascript
class CoffeeMachine {
  #waterAmount = 0; // Propiedad privada

  constructor(power) {
    this.power = power; // Propiedad pública
    console.log(`Cafetera creada con potencia: ${power}`);
  }

  setWaterAmount(amount) {
    if (amount < 0) {
      throw new Error("La cantidad de agua no puede ser negativa");
    }
    this.#waterAmount = amount;
  }

  getWaterAmount() {
    return this.#waterAmount;
  }
}

let coffeeMachine = new CoffeeMachine(100);
coffeeMachine.setWaterAmount(200); // Usamos el método público para establecer el valor
console.log(coffeeMachine.getWaterAmount()); // 200
```
#### <font color="#fdeada">Protegido</font>
Para propiedades y métodos que deben ser accesibles dentro de la clase y sus subclases, pero no desde fuera.
- **Accesible desde dentro de la clase y sus subclases.**
- **Ejemplo:** No hay soporte nativo en JavaScript, pero se puede emular usando convenciones como el prefijo `_`.
Usamos el prefijo `_` para indicar que una propiedad es protegida por convención.
```javascript
class CoffeeMachine {
  _waterAmount = 0; // Propiedad protegida por convención

  constructor(power) {
    this.power = power; // Propiedad pública
    console.log(`Cafetera creada con potencia: ${power}`);
  }

  setWaterAmount(amount) {
    if (amount < 0) {
      throw new Error("La cantidad de agua no puede ser negativa");
    }
    this._waterAmount = amount;
  }

  getWaterAmount() {
    return this._waterAmount;
  }
}

class AdvancedCoffeeMachine extends CoffeeMachine {
  constructor(power) {
    super(power);
  }

  increaseWater(amount) {
    this._waterAmount += amount; // Acceso permitido en la subclase
  }
}

let advancedCoffeeMachine = new AdvancedCoffeeMachine(200);
advancedCoffeeMachine.setWaterAmount(100);
advancedCoffeeMachine.increaseWater(50);
console.log(advancedCoffeeMachine.getWaterAmount()); // 150
```

### InstanceOf
El operador `instanceof` se utiliza para verificar si un objeto pertenece a una clase específica o a una clase que hereda de ella. Esto es útil para construir funciones polimórficas que tratan los argumentos de manera diferente según su tipo.
```javascript
class Animal {}
class Rabbit extends Animal {}

let rabbit = new Rabbit();

console.log(rabbit instanceof Animal); // true
```

#### Personalizacion con `Symbol.hasInstance`
```javascript
class Animal {
  static Symbol.hasInstance {
    return obj.canEat === true;
  }
}

let obj = { canEat: true };

console.log(obj instanceof Animal); // true
```
#### Con `Funciones` Constructoras
```javascript
function Rabbit() {}
let rabbit = new Rabbit();

console.log(rabbit instanceof Rabbit); // true
```

#### `Con` Funciones Integradas
```javascript
let arr = [1, 2, 3];

console.log(arr instanceof Array); // true
console.log(arr instanceof Object); // true
```
