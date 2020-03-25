## Node.js中异步API的实现方案
```js
/**
* 1.利用setTimeout函数实现异步操作
* 2.利用try...catch语句来实现错误的捕捉
* 3.将错误对象放在回调函数的第一个参数的位置(错误的回调优先原则)
* 
* */
/**
* 自定义一个用来将JSON字符串转换成js对象的异步功能函数
* 参数1.要转换的JSON字符串
* 参数2.回调函数
* */
function parseJSONAsync(string,callback) {
  setTimeout(function() {
    try {
      let obj = JSON.parse(string);
      //程序没有出错 回调函数的第一个参数就是null
      callback(null,obj)
    }catch (e) {
      //捕捉到错误 回调函数的第一个参数就是错误对象
      callback(e)
    }
  },0)
}

//测试
let str = '{"name":"林志玲","age":33}';  //非法的JSON格式的字符串
parseJSONAsync(str,function(err,data) {
  if(err){
    console.log('程序出错')
  }else{
    console.log(data)
  }
});
console.log('hello')
//结果会先打印：hello 然后打印：程序出错
```
