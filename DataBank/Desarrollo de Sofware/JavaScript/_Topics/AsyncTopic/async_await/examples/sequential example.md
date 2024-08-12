---
tags:
  - Ejercicios
---

```js
//tasks.js
const util=require('util);
const sleep = util.promisify(setTimeout//convierte funciones callback, a funciones que se pueden manejar con promesas o asyncawait

module.exports = {
	async taskOne(){
		await sleep(4000)
		return 'ONE VALUE'
	},
	async taskTwo(){
		await sleep(2000)
		return 'ONE VALUE'
	}
}
```

```js
//index.js
const {taskOne,tasktwo}= require('/.tasks')

async function main(){
	console.time("Measuring time")
	const valueOne=await taskOne();
	const valueTwo=await taskTwo();
	console.timeEnd("Measuring time");
	
	console.log('task'valueOne);
	console.log('task'valueTwo);
}
//Ambos se corren en 6 segundos, se corre uno despues de otro
```