Se utiliza para hacer referencia al objeto que está llamando a la función o al método. Este objeto a veces se llama contexto
```javascript
lass Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }

  calculateArea() {
    return this.height * this.width;  // Aquí, `this` se refiere al objeto Rectangle
  }
}

let myRectangle = new Rectangle(5, 10);
console.log(myRectangle.calculateArea());  // Imprime 50
```

#### Helpers

#### .call()
Este método llama a una función con un valor `this` dado y argumentos proporcionados individualmente.
```javascript
let persona = {
  nombre: 'Juan',
  saludar: function() {
    console.log(`Hola, mi nombre es ${this.nombre}`);
  }
}

let persona2 = {
  nombre: 'Ana'
}

persona.saludar.call(persona2);  // Salida: "Hola, mi nombre es Ana"
```

#### .apply()
Este método es similar a `.call()`, pero los argumentos de la función se pasan como un array.
```javascript
let persona = {
  nombre: 'Juan',
  saludar: function(ciudad, pais) {
    console.log(`Hola, mi nombre es ${this.nombre} y vivo en ${ciudad}, ${pais}`);
  }
}

let persona2 = {
  nombre: 'Ana'
}

persona.saludar.apply(persona2, ['Ciudad de México', 'México']);  // Salida: "Hola, mi nombre es Ana y vivo en Ciudad de México, México"
```

#### .bind()
Este método retorna una nueva función, permitiéndote especificar el valor de `this`.
```javascript
let persona = {
  nombre: 'Juan',
  saludar: function() {
    console.log(`Hola, mi nombre es ${this.nombre}`);
  }
}

let persona2 = {
  nombre: 'Ana'
}

let saludarAna = persona.saludar.bind(persona2);

saludarAna();  // Salida: "Hola, mi nombre es Ana"
```