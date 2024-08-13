Las promesas son objetos que representan el eventual resultado (o error) de una operación [[async_await]]. ^37359d

![[DiagramaPromises.png]]

```js
function requestHandler(req,res){
User.findById(req.userId)
	.then(function(user){ //cuando todo va bien
		returns Task.findById(user.tasksId)
	})
	.then(function (task){
		tasks.completed = true;
		return tasks.save();
	})
	.then(function(){
		res.send('Task completed')
	})
	.catch(function(err){ //cuando ocurre un error
		res.send(err);
	})
}
```

### <font color="#fdeada">Instance methods</font>

- **<font color="#d99694">then()</font>**: Este método se utiliza para especificar acciones a realizar cuando la promesa se resuelve exitosamente. Acepta dos argumentos, ambos son funciones de callback, la primera se ejecuta si la promesa se resuelve con éxito y la segunda si la promesa es rechazada.

- **<font color="#d99694">catch()</font>**: Este método se utiliza para manejar cualquier rechazo que ocurra en la promesa. Acepta una función de callback que se ejecuta cuando la promesa es rechazada.

- <font color="#d99694">**finally(</font>)**: Este método se utiliza para especificar acciones que se deben realizar independientemente de si la promesa fue resuelta o rechazada. Acepta una función de callback que se ejecuta cuando la promesa se resuelve o se rechaza.

```javascript
let promesa = new Promise((resolve, reject) => {
    let condicion = true;
    if(condicion) {
        resolve('La promesa fue resuelta');
    } else {
        reject('La promesa fue rechazada');
    }
});

promesa
    .then(response => console.log(response)) // Se ejecuta si la promesa se resuelve con éxito
    .catch(error => console.log(error)) // Se ejecuta si la promesa es rechazada
    .finally(() => console.log('Esto se ejecuta independientemente del resultado')); // Se ejecuta independientemente del resultado
```

### [[returnNewPromise()]]
![[returnNewPromise()#^587cfa]]

### [[promisificacion]]
![[promisificacion#^2cdedc]]
### <font color="#fdeada">methods</font>

#### 1-.Promise.all([])
 Todo lo que este dentro se ejecutara de forma paralela devolviendo una promesa.
 ```javascript
Promise.all([Promise.resolve(1), Promise.resolve(2), Promise.resolve(3)])
  .then(values => console.log(values)); // [1, 2, 3]
```
#### 2-.Promise.allSettled(iterable)
Lo mismo que promise pero devuelve un arreglo que describe el resultado de cada promesa.
```javascript
Promise.allSettled([Promise.resolve(1), Promise.reject('error'), Promise.resolve(3)])
  .then(results => console.log(results)); // [{status: 'fulfilled', value: 1}, {status: 'rejected', reason: 'error'}, {status: 'fulfilled', value: 3}]
```
#### 3-.Promise.any(iterable)
Devuelve una promesa tan pronto resuelva una promesa.
```javascript
Promise.any([Promise.reject('error1'), Promise.resolve(2), Promise.reject('error2')])
  .then(value => console.log(value)) // 2
  .catch(error => console.log(error));
```
#### 4-.Promise.race(iterable)
Lo mismo que arriba pero en cuento una promesa devuelva un rechazo regresa todo.
```javascript
Promise.race([Promise.resolve(1), Promise.reject('error'), Promise.resolve(3)])
  .then(value => console.log(value)) // 1
  .catch(error => console.log(error));
```
#### 5-.Promise.reject(reason)
Devuelve una promesa que es rechazada con la razon dada.
```javascript
Promise.reject('error').catch(error => console.log(error)); // 'error'
```
#### 6-.Promise.resolve.then(1)
Devuelve una promesa que es aceptada con la razon dada.
```javascript
Promise.resolve(1).then(value => console.log(value)); // 1
```

#### 7-.Promise.any()
 Toma un iterable de promesas (como un array) y devuelve una sola promesa. Esta promesa se cumple tan pronto como cualquiera de las promesas del iterable se cumpla. Si todas las promesas se rechazan, Promise.any() se rechaza con un AggregateError que contiene un array de todas las razones de rechazo.
Es útil cuando necesitas que al menos una de varias operaciones asíncronas se complete con éxito. Por ejemplo, podrías usarlo para intentar varias fuentes de datos y tomar la primera que responda correctamente.
```javascript
const p1 = new Promise((resolve, reject) => setTimeout(reject, 100, "Error en p1"));
const p2 = new Promise((resolve) => setTimeout(resolve, 200, "p2 resuelta"));
const p3 = new Promise((resolve) => setTimeout(resolve, 300, "p3 resuelta"));

Promise.any([p1, p2, p3])
  .then((value) => console.log(value)) // "p2 resuelta"
  .catch((error) => console.log(error.errors)); // Si todas las promesas se rechazan
```
