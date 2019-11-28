##window对象的方法

```js
//1.window.alert('要提示的内容');
window.alert('此操作暂时不支持');

//2.window.prompt('要显示的信息'[,'默认的内容']);
//该方法有返回值:
//如果用户点击了'取消'按钮，则返回值为null;
//如果点击了'确定'按钮，则返回值就是用户输入的内容;
let message = window.prompt('请输入你的名字');
if(message===null){
	//说明用户点击了取消按钮   
}else if(!message.trim().length){
  //说明用户输入的是无效内容
}else{
  //用户输入的内容有效
  console.log(message.trim());
}

//3.window.confirm('要提示的内容');
//该方法有返回值:
//如果用户点击了'确定'按钮，则返回值为true;
//如果用户点击了'取消'按钮，则返回值为false;
let result = window.confirm('确定删除该文件吗？');
if(result){
	//用户点击了确定按钮   
}else{
  //用户点击了取消按钮
}

//4.window.print(); 打印当前页面->或者将当前页面保存为pdf文件
```

