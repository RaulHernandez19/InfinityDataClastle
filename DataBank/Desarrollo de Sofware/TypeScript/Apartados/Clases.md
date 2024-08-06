```tsx
export class Person{
    //public name: string;
    //private address: string;

    constructor(
        public name: string,
        private address: string
        ) {}
        //this.name = name;
       // this.address=address;
}

//const ironman = new Person();

//console.log(ironman)

const ironman = new Person('Spiderman','New York')

console.log(ironman)
```

### Extender una clase

```tsx
export class Hero extends Person{//Va a acarrear todo lo de la otra clase
    
    constructor(
        public alterEgo: string,
        public age: number,
        public realName: string,
    ) {
        super(realName,'New York');
    }
}

const ironman = new Hero('Spiderman',17,'Peter Parker')
```
![[Untitled.png]]
### Priorizar composicion sobre herencia

```tsx
export class Hero{//Va a acarrear todo lo de la otra clase
    
//public person: Person;

//Con este cambio solo se vera afectada la clase persona si se cambia algo
    constructor(
        public alterEgo: string,
        public age: number,
        public realName: string,
        public person: Person,
    ) {
        this.person=new Person(realName,'New York');
    }
}

const tony = new Person('Peter Parker','New York')
const ironman = new Hero('Spiderman',17,'Peter Parker',tony)

console.log(ironman)
```