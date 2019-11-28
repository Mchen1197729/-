

原生Ajax的细节**

```js
//1.get请求 不传递参数
let url = 'http://localhost:3000';
let xhr = new XMLHttpRequest();
xhr.onload = function(){
  console.log(xhr.response);
};
xhr.onerror = function(){
  console.log('请求出错,请稍后重试~');
};
xhr.open('GET',url);
xhr.setRequestHeader("content-type", "application/x-www-form-urlencoded");
//一定要再xhr.open()之后设置才有效
xhr.responseType = 'json';
xhr.send();
```

```js
//2.get请求 传递参数:username='张三'
let url = 'http://localhost:3000';
let xhr = new XMLHttpRequest();
xhr.onload = function(){
  console.log(xhr.response);
};
xhr.onerror = function(){
  console.log('请求出错,请稍后重试~');
};
xhr.open('POST',url + '?username=张三');
xhr.setRequestHeader("content-type", "application/x-www-form-urlencoded");
//一定要再xhr.open()之后设置才有效
xhr.responseType = 'json';
xhr.send();
```

```js
//3.post请求 传递参数 username='张三'&password='123456'
let url = 'http://localhost:3000';
let xhr = new XMLHttpRequest();
xhr.onload = function(){
  console.log(xhr.response);
};
xhr.onerror = function(){
  console.log('请求出错,请稍后重试~');
};
xhr.open('POST',url);
xhr.setRequestHeader("content-type", "application/x-www-form-urlencoded");
//一定要再xhr.open()之后设置才有效
xhr.responseType = 'json';
xhr.send('username=张三&password=123456');
```

```js
//4.发送header头信息 user='cxk'
let url = 'http://localhost:3000';
let xhr = new XMLHttpRequest();
xhr.onload = function(){
  console.log(xhr.response);
};
xhr.onerror = function(){
  console.log('请求出错,请稍后重试~');
};
xhr.open('GET',url + '?username=张三');
//一定要再xhr.open()之后设置才有效
xhr.responseType = 'json';
xhr.setRequestHeader('user','cxk');
xhr.setRequestHeader("content-type", "application/x-www-form-urlencoded");
xhr.send();
```

```js
//服务器端跨域的设置 以express搭建服务器为例
let allowCrossDomain = function (req, res, next) {
  res.header('Access-Control-Allow-Origin', 'http://localhost:63342');
  res.header('Access-Control-Allow-Methods', 'GET,PUT,POST,DELETE');
  //res.header('Access-Control-Allow-Headers', 'Content-Type');
  //如果需要发送头信息,那么下面的配置也要添加上
  res.header('Access-Control-Allow-Headers', '*');
  res.header('Access-Control-Allow-Credentials', 'true');
  next();
};
```

