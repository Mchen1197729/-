##在使用input时避免浏览器的默认样式

```js
/*
思路：将input的display设置为none,然后自己创建一个div，设置为自己想要的样式,点击div时，主动触发input的click事件即可实现功能
*/
```

```html
<--样式代码-->
<style>
  #file{
    display:none;
  }  
</style>
<input type="file" id="file">
<button id="btn">选择文件</button>
<--js代码-->
<script>
	let fileInput = document.getElementById("file");
  let button = document.getElementById("btn");
  button.onclick = function(){
    //主动触发fileInput的点击事件
    fileInput.dispatchEvent(new MouseEvent("click"));
  };
  //监听fileInput的onchange事件
  fileInput.onchange = function(e){
    if(e.target.files.length){
      //打印选中的问价的文件名
       console.log(e.target.files[0].name);
    }else{
      //没有选择文件
      console.log("您还没有选择文件");
    }
  };
</script>  

```

