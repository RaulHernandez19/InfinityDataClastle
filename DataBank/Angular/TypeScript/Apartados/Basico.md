
--- start-multi-column: ID_ubo2
```column-settings
Number of Columns: 2
Largest Column: standard
```

## Variables
```tsx
const name: string = 'Strider';
let hpPoints: number | 'FULL' = 85;

/*En TS se puede tener una variable
que sea de un tipo o de otro, en este
caso tipo numero o exactamente la
palabra FULL
*/

hpPoints = 'FULL';

let v: any = true;
v = "string"; 
// no error as it can be "any" type

export{};
```

## Interface + Objeto
```tsx
const strider: Character = { 
name: 'Strider', 
hp: '100', 
skills: ['Bash','Counter'] }; 

strider.hometown='Subucador'
```

--- column-break ---

## Arrays
```tsx
const skills: string[] = [
'Suport',
'Tanque',
'DPS']
```

## Objeto
```tsx
const strider = {
name: 'Strider',
hp: '100',
skills: ['Bash','Counter']
};
```

--- end-multi-column






