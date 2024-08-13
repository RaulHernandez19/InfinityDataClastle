
## Array de objetos
Muchas veces cuando hagamos una soliciut de una API nos llegara mucho el formato de array de objetos.

```js
const arrayDeObjetos=[
{
	nombre: "David",
	edad: 23,
	comidaFav: "Tacos"
},
{
	nombre: "Sally",
	edad: 20,
	comidaFav: "Nada"
},
{
	nombre: "Steven",
	edad: 18,
	comidaFav: "Pizza"
}
]

//manera epica con forEach
arrayDeObjetos.forEach((persona)=>{
	conosle.log("Nombre"+persona.nombre);
	console.log("Edad"+persona.edad);
	conosle.log("Comida favorita"+persona.comidaFav);
});

//Manera Aburrida con for normalin
for (let i=0,i< arrayDeObjetos.lenght,i++){
	conosle.log("Nombre"+persona[i].nombre);
	console.log("Edad"+persona[i].edad);
	conosle.log("Comida favorita"+persona[i].comidaFav);
}
```

## Objeto con array
```js
const objetoConArray={
	nombre: "Objeto con arrray",
	arr: ["abeja","banana", "camion"]
}
objetoConArray.arr.forEach(elemento=>{
	console.log(elemento+"jaja");
})

```

