**监听屏幕的横屏竖屏**

```js
//利用js来监听手机横竖屏  ---> window.orientation即将被废弃
window.onload = function(){
    // window.orientation属性
    // 0度:手机是竖屏状态(默认状态)
    // 90度:手机是横屏状态
    console.log(window.orientation);
    // 监听横竖屏事件
    window.addEventListener('orientationchange',function(){
        console.log(window.orientation);
    });
};
```

**移动端适配**

```js
//移动端rem适配的代码
window.onload = function(){
  	let style = document.createElement('style');
    let width = document.documentElement.clientWidth;
    style.innerHtml = 'html{font-size:'+ width/16 +'px!important}';
    document.head.appendChild(style);
};
//这样屏幕的宽就是16rem 然后再结合less通过计算就可以实现“所量即所得”
```

```less
//设置less变量 假设设计稿的宽是720px
@rem:16rem/720px;
//这样设置以后,在设计稿上量取的长度假设为35px,name用rem单位来表示就是35/@rem;(所量即所得)
```

**事件的三个阶段**

```js
//事件分为三个阶段:1.捕获阶段 2.目标阶段 3.冒泡阶段
//1.捕获阶段:指事件从window对象开始依次向内层对象蔓延,window->document->html->body->父元素->元素自身
//2.目标阶段:指事件蔓延到绑定事件监听的元素本身
//3.冒泡阶段:指事件从元素本身依次向外层元素蔓延,元素自身->父元素->body->html->document->window
```

```html
<div class="wrap">
  <div class="inner">
    
  </div>
</div>
<script>
  //addEventListener('type',callback[,useCapture])
  // 第三个参数是表示是否监听捕获阶段,默认是false
	let inner = document.querySelector('.inner');
  inner.addEventListener('click',function(){
    console.log('11111');
  },true); // true表示监听的是捕获阶段的事件
  inner.addEventListener('click',function(){
    console.log('22222');
  },false); // false表示监听的是冒泡阶段的事件
  //如果点击了 打印顺序应该是 11111 22222
</script>
```

**事件代理的原理**

```html
<ul>
  <li>星期一</li>
  <li>星期二</li>
  <li>星期三</li>
  <li>星期四</li>
  <li>星期五</li>
  <li>星期六</li>
  <li>星期天</li>
</ul>
<script>
	let ul = document.querySelector('ul');
  //给父元素添加事件
  ul.addEventListener('click',function(e){
    let currentLi = e.target; //当前点击的li标签(不会有冒泡)
    let targetNode = this; //this是会冒泡的
    let ul = e.currentTarget; //绑定点击事件的元素
  });
</script>
```

```css
//设置元素不可见
display:none; //添加事件无效(不会触发) 不保留位置
visibility:hidden; //添加事件无效(不会触发) 保留位置
opacity:0; //添加事件有效(会触发) 保留位置
```

```js
//js数组的方法
let array = [1,2,3,4,5];
array.shift();   //返回被删除的元素-删除第一个元素
array.pop();     //返回被删除的元素-删除最后一个元素
array.push(7);   //返回新数组的长度-往数组末尾添加一个元素
array.unshift(8);//返回新数组的长度-往数组开头添加一个元素
```

**数组和对象的方法**

```js
let array = [1,2,3,4,5];
let data = array.values();
//array.values()返回的是iterator对象,必须用for-of来遍历
for(let val of data){
  console.log(val); //1 2 3 4 5
}
/*-------------------------------------------------*/
let per = {name:'蔡徐坤',age:28,hobby:'唱跳Rap篮球'};
let valueArr = per.values();
//per.values()返回的是对象所有可枚举的值组成的数组
let keyArr = per.keys();
//per.keys()返回的是对象所有可枚举的属性组成的数组
//不可枚举的属性及对应的值是不会显示在数组中的
```

**获取下拉框的内容**

```html
<select id="select">
  <option value="请选择城市" disabled>请选择城市</option>
  <option value="北京">北京</option>
  <option value="上海">上海</option>
  <option value="广州">广州</option>
</select>
<script>
	let select = document.getElementById('select');
  select.on('change',function(){
    //获取点击的option的下标 this.selectedIndex
    let index = this.selectedIndex;
    //获取点击的option的值 this.options[index].value
    let city = this.options[index].value;
  });
</script>
```

**创建对象的三种方式**

```js
//1.对象字面量的方式
let student = {name:'蔡徐坤',age:28};

//2.通过构造函数来创建对象
let student = new Student('蔡徐坤',28);

//3.通过Object.create()方法来返回一个对象
let per1 = {name:'林志玲'};
let per2 = Object.cteate(per1,{
  sex:{
    value:'女',
    configurable:false,
    writable:false,
    enumerable:false
  }
});
//per2:{name:'林志玲',sex:'女'}
```

**让脚本停止一段时间**

```js
let nowTime = Date.now();
while(Date.now()-nowTime>3000){
	  //在这3秒内什么都不做 相当于脚本停止了3秒
}
```

**标准盒模型和怪异盒模型**

```css
//标准盒模型总宽度 = width + padding-left + padding-right
//标准盒模型总高度 = width + padding-top + padding-bottom

//怪异盒模型总宽度 = width
//怪异盒模型总高度 = height
div{
  box-sizing:content-box; //标准盒模型 IE
  box-sizing:border-box;  //怪异盒模型 Chrome(推荐使用)
  width:100px;
  height:100px;
  padding:10px;
  margin:10px;
}
```

