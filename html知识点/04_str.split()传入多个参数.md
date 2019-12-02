### 字符串的split()方法传入多个参数
```js
// 以某一种符号作为分隔符
let str = 'hello,world';
console.log(str.split(','));  //['hello','world']
// 以多种符号作为分隔符
let dataURL = 'data:text/plain;base64,aGVsbG8gd29ybGQ=';
// 传入一个正则对象 用来匹配多个分隔符
console.log(dataURL.split(/[:;,]/)); //['data','text/plain','base64','aGVsbG8gd29ybGQ=']
```
