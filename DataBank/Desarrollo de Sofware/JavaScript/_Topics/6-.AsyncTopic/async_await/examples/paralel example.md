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
	const results = await Promise.all([taksOne(),taksTwo()])
	
	console.timeEnd("Measuring time");
	
	console.log('task',results[0]);
	console.log('task',results[1]);
}
//Ambos se recorren en paralelo en 4 segundos, si hay algun error no epxlota, simplemente lo otro no ocurre y lo otro si