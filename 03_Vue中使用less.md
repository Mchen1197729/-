## 在Vue单文件中使用less编写样式

```shell
#引入包
npm install less --save-dev  
npm install less-loader --save-dev  
```

less引用写法

```html
<template>
	<div class="container">
  	<div class="header">
      
  	</div>
  </div>
</template>
<script>

</script>
<style lang="less">
  .container{
    width:100%;
    height:100%;
    background-color:pink;
    .header{
      width:100px;
      height:100px;
      margin:100px auto;
    }
  }
</style>
```



