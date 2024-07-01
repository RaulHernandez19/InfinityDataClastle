> Super set de java Script ofreciendo: tipado estricto y flexible, mejorar la normalidad del codigo y caracteristicas modernas.

```tsx

//Ejemplo funcion
function calculaISV(productos: Producto[]):[number, number]{

let total = 0;

productos.forEach(({precio})=>
total+=precio;
)

return [total, total*0.15]
}
```
```tsx
//Clase en typeScript

class Persona {
nombre:string;
edad: number

constructor(){}
}
```

# Indice

- Basico
	- [[Basico]]
	
	- [[Funciones]]
	
	- [[Desestructuracion]]
	
	- [[Import-Export]]
	
	- [[Encadenamiento Opcional]]
	
- Relacionado Angular
	- [[Clases]]
	
	- [[Decoradores-TypeScript]]
	

#Lenguaje