**用express搭建后台服务器设置cors的方法**

```shell
#初始化
npm init --yes
#安装依赖
npm i express
```

```js
//app.js文件
const express = require('express');
const app = express();

//设置cors中间件
let allowCrossDomain = function(req,res,next){
  //允许访问的域名
  res.header('Access-Control-Allow-Origin','http://localhost:66342');
  //允许请求的方法
   res.header('Access-Control-Allow-Methods','GET,PUT,POST,DELETE');
  //允许请求的Headers
  res.header('Access-Control-Allow-Headers','Content-Type');
  //允许请求的Credentials
  res.header('Access-Control-Allow-Credentials', 'true');
};

//使用该中间件
app.use(allowCrossDomain);

//设置
app.get('/',(req,res)=>{
  res.send({
    code:'OK',
    data:{
      msg:'Hello Express'
    }
  });
});

app.listen(3000,()=>{
  console.log('app is running at port 3000...');
});
```

```html
<script>
	let xhr = new XMLHttpRequest();
  //设置响应的数据格式
  xhr.responseType = 'json';
	xhr.onload = function(){
    console.log(xhr.response.data); //{msg:'Hello Express'}
  };
  xhr.open('GET','http://localhost:3000');
  xhr.send();
</script>
```

