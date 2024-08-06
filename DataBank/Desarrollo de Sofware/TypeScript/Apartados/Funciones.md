## Funciones comunes

```tsx
function  addNumbers(a:number,b:number){
return a+b;}

const result:number = addNumbers(1,2)
console.log({result})

export{};
```

## Funciones de flecha ⇒

```tsx
function  addNumbers(a:number,b:number): string =>{
return '${a+b}'; //No so esas comillas, son las que son diagonales y chiquitas
}

const result:string= addNumbers(1,2)
console.log({result})

export{};
```

## Funciones multiply

```tsx
function multiplicacion(a:number,b?:number,base: number =2): number=>{
return a*base:
}

const result:number= addNumbers(1)
console.log({result})

export{};
```

## Funciones con objetos como argumentos

```tsx
interface Character{
name:string;
hp:number;
showHp: () => void;
}

const healCharacter = (character:Character, amount: number)=>{
character.hp+=amount;
}

const strider:Character {
	name: 'strider',
  hp: 50,
  showHp(){
		console.log('Puntos de vida ${this.hp}');//Aqui van las comillas feas
	}
}

healCharacter(strider, 30)

strider.showHp();
```

[[Ejercicio funciones]]

