```tsx
export interface Passenger{
    name: string;
    children?: string[];
}

const passenger1: Passenger = {
    name: 'Fernando',
}

const passenger2: Passenger = {
    name: 'Melissa',
    children: ['Natalia','Elizabeth'],
}

const returnChildrenNumber=(passenger: Passenger)=>{
    const {name:nombre} = passenger;

    const howManyChildren = passenger.children?.length || 0; //opcional chaining

    console.log(nombre,howManyChildren)
    return howManyChildren;
}

returnChildrenNumber(passenger1)
```
