**pointer-events属性**

```html
<-- pointer-events属性用来设置元素对鼠标的事件的反应 -->
<-- 对于Html此属性的值只有两个有用：none,auto -->
<style>
  .silent-click{
    pointer-events:none; //表示该元素不响应鼠标的事件
  }  
</style>  
<body>
  <button id="btn">按钮</button>
  <script>
    //使用场景：防止用户多次点击按钮导致请求重复提交
  	let btn = document.getElementById('btn');
    btn.onclick = function(){
      console.log('鼠标点击按钮');
      //让该元素不响应鼠标的事件
      btn.classList.add('silent-click');
      setTimeout(()=>{
        //设置定时器，三秒钟后让该元素恢复响应鼠标的事件
        btn.classList.remove('silent-click');
      },3000);
    };
  </script>
</body>
```

