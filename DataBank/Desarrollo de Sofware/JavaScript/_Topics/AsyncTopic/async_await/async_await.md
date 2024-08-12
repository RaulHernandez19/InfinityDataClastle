
```js
async function requestHandler(req,res){
	try{
		const user = await User.findById(req.userId);
		const tasks = await Task.findById(user.tasksId);
		task.completed=ture:
		await tasks.save();
		res.send('taks completed')
	}catch(e){
		res.send(e)
	}
}
```
Await solo esta disponible en funciones async.

### Examples
###### [[paralel example]]
###### [[sequential example]]



