**webpack学习记录**
		**1.webpack中四个重要的概念**

​		**entry,output,loader,plugin**

**entry**:表示程序打包的入口文件

**output**:表示打包后生成的文件的配置，有两个属性：filename,path

**loader**:webpack本身只能处理js和json文件，如果需要处理其他类型的文件则需要用到对应的loader

**plugin**:提供更加强大的功能

**起步：**

```shell
#安装依赖
npm init --yes #生成package.json文件

npm install webpack --save-dev
npm install webpack-cli --save-dev

#修改package.json文件
"scripts": {
    "start": "webpack --config webpack.config.js"
}
#加上这一行
+"private":true,
#删除这一行
-"main":"index.js",
#文件目录结构
webpack-demo
	|- package.json
	|- index.html
	|- /src
		|- index.js
	|-webpack.config.js	
```

```js
//webpack.config.js
const path = require('path');

module.exports = {
  //入口：表明webpack从该文件处开始执行打包任务
  entry:'./src/index.js',
  //出口：webpack打包完成后将打包后的内容存放在哪里
  output:{
    filename:'bundle.js',
    path:path.resolve(__dirname,'dist')
  }
};
```

```shell
#执行命令：npm start
#会在当前文件夹下生成一个dist目录,里面有一个文件bundle.js,在index.html中将该文件引入即可。
```

**管理资源：**

```shell
#加载css文件
npm install --save-dev style-loader
npm install --save-dev css-loader
#添加样式文件
webpack-demo
	|- package.json
	|- index.html
	|- /src
		|- index.js
	  |- index.css #新增
	|-webpack.config.js	
```

```js
//修改webpack.config.js文件
//webpack.config.js
const path = require('path');

module.exports = {
  //入口：表明webpack从该文件处开始执行打包任务
  entry:'./src/index.js',
  //出口：webpack打包完成后将打包后的内容存放在哪里
  output:{
    filename:'bundle.js',
    path:path.resolve(__dirname,'dist')
  },
  //新增loader部分
  module:{
    //规则都写在modules.rules属性中
    rules:[
      {
        test:/\.css$/,
        //use数组的解析顺序是从后往前：
        //先利用css-loader将index.js中引入的css文件
        use:['style-loader','css-loader']
      }
    ]
  }
};
```

```shell
#加载less文件
npm install --save-dev less-loader 
npm install --save-dev less
#添加样式文件
webpack-demo
	|- package.json
	|- index.html
	|- /src
		|- index.js
	  |- index.css #新增
	  |- index.Less #新增
	|-webpack.config.js	
```

```js
//修改webpack.config.js
//webpack.config.js
const path = require('path');

module.exports = {
  //入口：表明webpack从该文件处开始执行打包任务
  entry:'./src/index.js',
  //出口：webpack打包完成后将打包后的内容存放在哪里
  output:{
    filename:'bundle.js',
    path:path.resolve(__dirname,'dist')
  },
  //新增loader部分
  module:{
    //规则都写在modules.rules属性中
    rules:[
      {
        test:/\.css$/,
        use:['style-loader','css-loader']
      },
      //新增Less文件的解析规则
      {
        test:/\.Less$/,
        use:['style-loader','css-loader','less-loader']
      }
    ]
  }
};
```

