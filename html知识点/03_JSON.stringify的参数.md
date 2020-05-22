**JSON.stringify()的参数问题**

```js
//1.基础用法
let data = {name:'林志玲',age:49};
console.log(JSON.stringify(data));  //字符串:{'name':'林志玲','age':49}
let arr = [1,2,'hello'];
console.log(JSON.stringify(arr));  //字符串:[1,2,'hello']
```

```js
//2.第二个参数:可以是一个函数(用于对序列化的值进行处理),也可以是一个数组(用于确定哪些属性需要被序列化)
let data = {name:'林志玲',age:49,married:true};
let dataStr = JSON.stringify(data,(key,value)=>{
  switch(key){
    case 'name':
      return value+value;  //对对应的值做出处理
    case 'age':
      return value-10;    //对对应的值做出处理
    case 'married':
      return undefined;   //return undefined说明要跳过该属性的序列化
    default:
      return value; //必须要将value返回才能有值
     }
});
//dataStr:{'name':'林志玲林志玲','age':39}

let dataStr2 = JSON.stringify(data,['name','age']); //只序列化name和age属性
//dataStr2:{'name':'林志玲','age':49}
```

```js
//第三个参数(传入一个数字,用来指定序列化后的字符串的缩进格式,也可以传入一个字符串,用来指定分隔符)
//如果传入的是数字 那么数字最多是10 多了无效
let data = {name:'林志玲',age:49,married:true};
let dataStr = JSON.stringify(data,null,2);
/*
dataStr:
{
	'name':'林志玲',
	'age':49,
	'married':true
}
*/
//如果传入字符串 那么字符串的长度最多10位 多余的无效
let dataStr2 = JSON.stringify(data,null,'|-');
/*
{
|-'name':'林志玲',
|-'age':49,
|-'married':true
}
*/
```

```js
//使用JSON.stringify()时的注意点
//1.对象中的undefined,任意Symbol值,函数是不能被序列化的
let data = {
  name:undefined,
  sayHi:function(){
  	console.log('你好');
	},
  id:Symbol('1001')
};
let dataStr = JSON.stringify(data); // {}

//2.数组中的undefined,任意Symbol值,函数会被转换成null
let arr = [
  undefined,
  function(){
  	console.log('你好');
	},
  Symbol('1001')
];
let arrStr = JSON.stringify(data); // [null,null,null]

//3.如果被序列化的对象中有toJSON方法,那么序列化的值就是toJSON方法的返回值
let obj = {
  name:'林志玲',
  age:49,
  toJSON(){
    return {
      name:'波多野结衣',
      married:false
    }
  }
};
let objStr = JSON.stringify(obj); // 结果:{"name":"波多野结衣","married":false}
```

