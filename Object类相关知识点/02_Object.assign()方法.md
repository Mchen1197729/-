## Object.assign()方法
>1.Object.assign(target,...source)
    可以接受多个源对象 最后返回值也是新的对象
```js
const obj = Object.assign({},{name:'林志玲'},{age:28},{isMarried:true});
console.log(obj); //{name:'林志玲',age:28,isMarried:true}
```
