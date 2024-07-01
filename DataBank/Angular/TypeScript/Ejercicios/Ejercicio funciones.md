```tsx
interface Adress{
street: string;
city: string;
country: string;
}

interface SuperHero{
name: string;
age: number;
adress: Adress;
showAdress: () => string;
}

const superHeroe: SuperHero = {
name: spiderman,
age: 20,
adress:{
	street: 'Brooklyn',
	city: 'NY',
	country: 'USA'
},
showAdress(){
	return this.name;
}
}

const adress = superHeroe.showAdress();
console.log(adress);
```

#Ejercicios