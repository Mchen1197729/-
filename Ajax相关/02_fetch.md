**用fetch来发送ajax请求**

```js
//1.只传入一个访问的地址
let url = 'http://localhost:3000';
fetch(url)
	.then((response)=>{
  //response.json()是一个promise对象,将该promise对象返回出去,就可以链式调用了
  return response.json();
})
	.then((res)=>{
  //res就是服务器返回的数据
  console.log(res);
})
	.catch(()=>{
  console.log('请求出错,请重试~');
});
```

```js
//2.传入配置选项
let url = 'http://localhost:3000/login';
fetch(url,{
  method:'POST',
  headers:{
    'content-type': 'application/json',
  },
  //如果content-type设置成了application/json的话，传递请求体参数就一定要传递json字符串
  body:JSON.stringify({username:'林志玲',age:29})
})
	.then(response=>{
  return response.json();
})
	.then(res=>{
  console.log(res);
})
	.catch(()=>{
  console.log('请求出错,请重试~');
})
```

```js
//3.传入配置选项
let url = 'http://localhost:3000/login';
fetch(url,{
  method:'POST',
  headers:{
    'content-type': 'application/x-www-form-urlencoded',
  },
  //如果content-type设置成了application/x-www-form-urlencoded的话，
  //传递请求体参数就一定要传递querystring字符串。
  body:'username=林志玲&age=29'
})
	.then(response=>{
  return response.json();
})
	.then(res=>{
  console.log(res);
})
	.catch(()=>{
  console.log('请求出错,请重试~');
})
```

