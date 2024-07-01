```tsx

//export
export function taxCalculation(options: TaxCalculationsOptions): number[]{
    const{tax,products}=options;

    let total=0;

    products.forEach(({price})=>{
        total+=price;
    });

    return [total,total * tax]
}
-----
//import y desestructuracion
import {Product,taxCalculation} from './06-function-destructuring'

```