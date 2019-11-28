**在express中使用art-template模板引擎**

```shell
npm install --save art-template
npm install --save express-art-template
```

```js
const express = require('express');
const app = express();

//默认渲染的是views文件夹中的index.html页面
app.engine('html',require('express-art-template'));
app.get('/',(req,res)=>{
  res.render('index.html'); //views文件夹下的index.html文件
});
```

