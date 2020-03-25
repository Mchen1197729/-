## 微信小程序wepy框架的使用踩坑

### 2020-03-24日接触wepy小程序框架 第二天开始自己创建项目
>1.报错：找不到编译器：wepy-compiler-less。未发现相关 less 编译器配置，请检查wepy.config.js文件。
   解决：npm install less 并且 npm install wepy-compiler-less之后完美解决

>2.报错：使用async出现regeneratorRuntime is not defined错误
   解决：网上都是说打开微信开发者工具的es6转es5和增强编译选项就可以了 可是我关闭了这两个选项了之后反而在可以解决问题
