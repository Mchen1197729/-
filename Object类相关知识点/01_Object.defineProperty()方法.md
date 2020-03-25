## Object.defineProperty方法
>   Object.defineProperty(obj,prop,descriptor) 返回当前对象
    参数1.对象实例
    参数2.对象的属性
    参数3.属性描述对象
          属性描述器分为两类：1.存取描述符 2.数据描述符 (二者不能同时存在)
          
```js
// 数据描述符
let per = {name:'林志玲'};
Object.defineProperty(per,'age',{
  value:33, // 添加的属性的值
  writable:true, //该属性是否可以修改或者重新赋值 per.age++ 或者per.age = 55
  configurable:true, // 该属性是否可以被删除 delete per.age 或者重新定义Object.defineProperty(obj,prop,{})
  enumerable:true // 该属性是否可以遍历(for-in、keys())
});

// 存取描述符
let stu = {firstName:'Cris',lastName:'Paul'};
Object.defineProperty(stu,'fullName',{
  get(){
    return this.firstName + '--' +this.lastName;
  },
  set(value){
    let arr = value.split('--');
    this.firstName = arr[0];
    this.lastName = arr[1];
  }
});
```          
