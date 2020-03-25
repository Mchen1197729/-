## 关于vue-cli教授的不同版本的一些总结

### vue-cli 2.x版本
    全局安装：npm install -g vue-cli
    生成项目：vue init 模板名 项目名 
        例如：vue init webpack vue-draw (以webpack为模板 项目名称为vue-draw)
        
        
### vue-cli 3.x版本
    全局安装：npm install -g @vue/cli        
    生成项目：vue create 项目名
        例如：vue create vue-draw
    除此之外还可以通过图形化界面的方式来创建一个新的项目
        打开图形化界面：vue ui (该命令会打开本地的浏览器进入图形化的界面 可以自己选择需要的服务)    
        
        
### 如果全局安装了3.x的版本以后还想生成2.x版本的项目 则需要安装一个桥接工具
     全局安装：npm install -g @vue/cli-init
     生成项目：vue init 模板名 项目名 (跟2.x版本生成的项目是一致的)        
