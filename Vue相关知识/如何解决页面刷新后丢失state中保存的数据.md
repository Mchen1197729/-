## 如何解决页面刷新后丢失state中保存的数据
```vue
<template>

</template>
<script>

export default {
  name:'App',
  //组件创建后去读取sessionStorage中保存的state数据
  created(){
    if(sessionStorage.getItem('state')){
      // Object.assign(target,...source)
      this.$store.replaceState(Object.assign({},this.$store.state,JSON.parse(sessionStorage.getItem('state'))))
    }
    
    //在页面刷新前 将state中的数据保存到sessionStorage中
    window.addEventListener('beforeunload',()=> {
      sessionStorage.setItem('state',JSON.stringify(this.$store.state))
  })
  },
}
</script>
<style>

</style>

```
