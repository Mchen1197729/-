## 在Vue框架中使用Vuex

```shell
#|--store目录
#--|--index.js 
#--|--state.js
#--|--actions.js
#--|--mutations.js
#--|--getters.js
#--|--mutation-types.js
```

```js
//state.js
export default {
  //这里面写每一个state状态
  todoList:[],
  counter:0
}
```

```js
//mutation-types.js
export const ADD_TODO = 'add_todo'
export const DELETE_TODO = 'delete_todo'
```

```js
//actions.js
import {
  ADD_TODO,
  DELETE_TODO
} from './mutations-types'
export default {
  //新增一项任务
  addTodo({commit},{id,title,completed}){
    commit(ADD_TODO,{id,title,completed})
  },
  //删除一项任务
  deleteTodo({commit},{id}){
    commit(DELETE_TODO,{id})
  },
  //......
}
```

```js
//mutations.js
import {
  ADD_TODO,
  DELETE_TODO
} from './mutations-types'
export default {
  //修改state中的状态
  //新增
  [ADD_TODO](state,{id,title,completed}){
    //最好不要直接修改原来的状态值，而是产生新的状态值
    // 不要直接修改属性 要重新赋值
    state.todoList = [...state.todoList,{id,title,completed}]
  },
  //删除
  [DELETE_TODO](state,{id}){
    //最好不要直接修改原来的状态值，而是产生新的状态值
    // 不要直接修改属性 要重新赋值
    state.todoList = state.todoList.filter(item=>{
      return item.id!==id
    })
  }
}
```

```js
//getters.js
//getters就相当于state的计算属性
export default {
  todoCount(state){
    return state.todoList.length
  }
}
```

```js
//index.js
import Vue from 'vue'
import Vuex from 'vuex'

//mutation-types文件不需要引入
import state from './state'
import actions from './actions'
import mutations from './mutations'
import getters from './getters'
//声明使用Vuex
Vue.use(Vuex)

//直接导出store对象
export default new Vuex.Store({
  state,
  actions,
  mutations,
  getters
})
```

```js
/*在入口文件main.js中声明全局的store对象*/
import store from './store/index'
new Vue({
  el: '#app',
  router,
  store,  //声明全局的store对象
  components: {App},
  template: '<App/>'
})
```



## 在Nuxt.js中使用Vuex

```shell
#|--store目录
#--|--index.js #有区别
#--|--state.js #有区别
#--|--actions.js
#--|--mutations.js
#--|--getters.js
#--|--mutation-types.js
```

```js
//state.js
//此时state.js应该导出有个function,而function 的返回值是state对象
//而且推荐使用箭头函数书写
export default ()=>({
  todoList:[],
  count:0
})
```

```js
//index.js
import Vue from 'vue'
import Vuex from 'vuex'

//mutation-types文件不需要引入
import state from './state'
import actions from './actions'
import mutations from './mutations'
import getters from './getters'
//声明使用Vuex
Vue.use(Vuex)

//此时index.js文件必须导出一个function,此function返回一个store对象
//推荐使用箭头函数书写
export default () => (new Vuex.Store({
  actions,
  state,
  mutations,
  getters
}))
```

```js
/*在入口文件main.js中声明全局的store对象*/
import store from './store/index'
new Vue({
  el: '#app',
  router,
  store,  //声明全局的store对象
  components: {App},
  template: '<App/>'
})
```



