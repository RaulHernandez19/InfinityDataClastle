## Objetos

```tsx
interface AudioPlayer{
    audioVolume: number;
    songDuration: number;
    song: string;
    details: Details;

}

interface Details {
    author: string;
    year: number;
}

const audioPlayer: AudioPlayer = {
    audioVolume: 90,
    songDuration: 36,
    song: "Mess",
    details: {
        author: "Lady Gaga",
        year: 1829
    }
}
//Forma incorrecta
console.log('Song: ',audioPlayer.song)
console.log('Song: ',audioPlayer.details.author)

//Ahora sacaremos partes que nos interesen con desestructuracion

const song = 'New Song';
const {
    song:anothersong,
    songDuration:duration,
    details:{author}
} = audioPlayer

console.log('Song epica: ',anothersong)
console.log('Duracion epica: ',duration)
console.log('Author epica: ',author)

export{}
```

## Arreglos

```tsx
const dbz: string[]=['Goku','Vegeta','Trunks'];
const vulma = dbz[3] || 'No Hay personaje aaaaaaa';

//Desestructuracion meh
console.log('Personaje 3:', dbz[5] || 'No hay personaje')

const [, , trunks]=['Goku','Vegeta','Trunks'];

console.log(trunks)
```

## Argumentos

```tsx
interface Product {
    description: string,
    price: number
}

const phone: Product = {
    description: 'Nokia A1',
    price: 150.0
}

const tablet: Product = {
    description: 'iPad Air',
    price: 250.0
}

interface TaxCalculationsOptions {
    tax: number;
    products: Product[];
}

function taxCalculation(options: TaxCalculationsOptions): number[]{
    let total=0;

    options.products.forEach(product=>{
        total+=product.price;
    });

    return [total,total * options.tax]
}

const shoppingCart=[phone,tablet];
const tax = 0.15

const result = taxCalculation({
    products: shoppingCart,
    tax: tax
})

console.log('Total',result[0])
console.log('Tax',result[1])

export {}
```

```tsx
//Version con desestructuracion avanzada

interface Product {
    description: string,
    price: number
}

const phone: Product = {
    description: 'Nokia A1',
    price: 150.0
}

const tablet: Product = {
    description: 'iPad Air',
    price: 250.0
}

interface TaxCalculationsOptions {
    tax: number;
    products: Product[];
}

function taxCalculation(options: TaxCalculationsOptions): number[]{
    const{tax,products}=options;

    let total=0;

    products.forEach(({price})=>{
        total+=price;
    });

    return [total,total * tax]
}

const shoppingCart=[phone,tablet];
const tax = 0.15

const result = taxCalculation({
    products: shoppingCart,
    tax: tax
})

//Desestructurado
const { description:Tabletdesc, price:Tabletprice }=tablet
const [taxproducts,rtax] = result

console.log("Tablet: ",Tabletdesc)

console.log('Taxproducts',taxproducts)
console.log('Tax',rtax)
//console.log('Tax',result[0])
//console.log('Tax',result[1])

export {}
```