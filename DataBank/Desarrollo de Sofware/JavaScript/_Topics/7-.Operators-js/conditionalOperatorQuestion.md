Util para hacer if cortos y consisos.

```js
//Antes
let accessAllowed;
if (age > 18) {
  accessAllowed = true;
} else {
  accessAllowed = false;
}
//Despues
let accessAllowed = (age > 18) ? true : false;
//En este caso especifico tambien puede ser asi
let accessAllowed = age > 18;
```

## Multiple ?
Tambien se puede usar para escribir varias condicionales

```js
//Antes
if (age < 3) {
  message = 'Hi, baby!';
} else if (age < 18) {
  message = 'Hello!';
} else if (age < 100) {
  message = 'Greetings!';
} else {
  message = 'What an unusual age!';
}
//Despues

let age = prompt('age?', 18);

let message = (age < 3) ? 'Hi, baby!' :
  (age < 18) ? 'Hello!' :
  (age < 100) ? 'Greetings!' :
  'What an unusual age!';
  
console.log(message);
```

## Minis task
```js
//#1
let result = (a+b < 4) ? 'Below' : 'Over';
//#2
let login;
let message = (login=='Employee') ? 'Hello' :
			  (login=='Director') ? 'Greetings' :
			  (login=='') ? 'No login' :
			  ''
```