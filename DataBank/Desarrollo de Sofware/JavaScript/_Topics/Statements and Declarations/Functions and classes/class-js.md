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

### <font color="#d99694">Extension de clases</font>
JavaScript permite la herencia de clases mediante la palabra clave extends. Por ejemplo, si tienes una clase Rectangle, puedes crear una clase FilledRectangle que herede de Rectangle.
```javascript
class FilledRectangle extends Rectangle {
  constructor(height, width, color) {
    super(height, width);  // Llama al constructor de la clase padre
    this.color = color;
  }
}
```

#### Super()
Se utiliza en el constructor de una subclase para llamar al constructor de la clase padre.

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