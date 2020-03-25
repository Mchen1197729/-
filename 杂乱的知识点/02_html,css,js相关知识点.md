## 宏任务和微任务 

```js
//js是单线程执行的,首先执行的是主宏任务队列,当主宏任务队列执行完后会判断是否有微任务
//宏任务队列可以有多个,但是微任务队列只有一个
//如果有微任务会执行微任务队列;如果没有微任务则执行其他宏任务队列
//setTimeout() setInterval()的回调函数被添加到宏任务队列中
//new Promise() 是同步执行的,但是promise.then()是异步执行的,并且被添加到微任务中
	console.log('start') //同步执行
  setTimeout(() => {
    console.log('timeout') //添加到宏任务队列
  }, 0)
  new Promise((resolve, reject) => {
    for (let i = 0; i < 5; i++) {
      console.log(i)
    } //同步执行
    resolve()
  }).then(() => { //异步执行,被添加到微任务队列
    console.log('promise')
  })
	console.log('end') //同步执行
//打印顺序 
// start 
// 0 1 2 3 4
// end
// promise
// timeout
```

## 改变浏览器默认的滚动条样式 

```css
/*滚动条样式*/
    body::-webkit-scrollbar {/*滚动条整体样式*/
      position: absolute;
      right: 0;
      /*修改width和height的值来控制粗细*/
      width: 5px;     /*高宽分别对应横竖滚动条的尺寸*/
      height: 5px;
    }
    body::-webkit-scrollbar-thumb {/*滚动条里面小方块*/
      border-radius: 5px;
      -webkit-box-shadow: inset 0 0 5px rgba(0,0,0,0.2);
      background: rgba(0,0,0,0.2);
    }
    body::-webkit-scrollbar-track {/*滚动条里面轨道*/
      -webkit-box-shadow: inset 0 0 5px rgba(0,0,0,0.2);
      border-radius: 0;
      background: rgba(0,0,0,0.1);
    }
```

## 滑动到页面最底部 

```js
//滚动到页面中的某个坐标的位置
//window.scrollTo(x-coord,y-coord )
//window.scrollTo(options)  
//options:{top:xxx,left:xxx,behavior:'smooth'||'instant'}  
//top等价于y-coord,left等价于y-coord
//behavior类型String,表示滚动行为,支持参数 smooth(平滑滚动),instant(瞬间滚动),默认值auto,实测效果等同于instant

window.onload = function(){
  window.scrollTo({
    top:document.body.scrollHeight, //滑动到页面最底部
    behavior:'smooth' //平稳滑动 如果不写则是立刻滑动到页面最底部
  });
};
```

## 正常的网页加载顺序 

```js
//1.浏览器一边下载html代码,一边开始解析;
//2.如果遇到<script>标签则暂停解析html代码,开始调用js引擎解析js代码;
//3.如果<script>标签引用了外部的js代码,则将代码下载下来,然后开始解析js代码;
//4.js代码解析完成后,继续解析html代码;
//5.如果外部js脚本加载时间很长,则会造成浏览器的卡顿->"浏览器的假死状态";
```

```html
<script src="index.js" defer>
//defer表示推迟该标签的解析,知道DOM结构渲染完成才开始解析该标签
//只能用于外部引用的文件
</script>
<script src="index.js" async>
//async表示开启另一个线程去解析该标签,与此同时渲染页面正常进行
//只能用于外部引用的文件
</script>
```

## 获取随机字符串

```js
let str = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789'
let strArr = str.split('')
strArr.sort(()=>{
  return Math.random() - 0.5
})
str = strArr.join('')
let randomStr = str.substr(0,8) //从下标为0开始,截取8位长度
```

