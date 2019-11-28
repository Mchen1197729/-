```shell
#git常用的命令
git config --global user.name "username" #配置用户名
git config --global user.password "xx@gmail.com" #配置邮箱
git init #初始化生成一个本地仓库
git clone url #将远程仓库克隆下载到本地 
git add * #添加到暂存区
git add . #将当前文件夹下所有文件都添加到暂存区
git commit –m "message" #提交到本地仓库(添加说明) 
git remote add origin url #关联到远程仓库
####重要
git remote rm origin  #删除与远程仓库的关联关系
git push origin -u master #push到关联的远程仓库
####重要
git pull origin master #从远程关联的仓库pull更新
```

