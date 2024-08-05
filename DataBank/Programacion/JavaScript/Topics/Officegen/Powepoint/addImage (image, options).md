>Just pass the image file name as the first parameter to addImage and the 2nd parameter, which is optional, is normal options objects and you can use all the common properties ('cx', 'cy', 'y', 'x', etc).

```js
slide.addImage('resources/template1.png', { x: 'c', y: 'c', cx: '100%', cy: '100%' });
```
