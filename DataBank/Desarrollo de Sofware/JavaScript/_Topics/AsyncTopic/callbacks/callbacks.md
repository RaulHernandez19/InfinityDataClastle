El callback es la madre de las funciones asincronas

```js
function requestHandler(req, res){
	User.fundById(req.userId, function(err, user)){ 
		if(err){
			res.send(err);
		}else{
			Tasks.findById(user.taskId,function(err,tasks))
				if(err){
					return res.send(err)
				}else{
					task.completed=true;
					task.save(function(err){
						if(err){
							return res.send(err);
						}else{
						res.send('Task completed')}
					})
				}
		}
	}
} 
```
Este codigo toma tiempo de ejecucion, La funcion de al lado que es otro parametro espera por la respuesta, las function seria los callbacks.