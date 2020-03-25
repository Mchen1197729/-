### Node中的一些知识点

#### 一.process全局对象
    1.process.argv 该值是一个数组 默认情况下数组的前两项是固定的
      process.argv[0] 是node.exe的安装路径(绝对路径)
      process.argv[1] 是当前被执行的脚本所处的文件路径(绝对路径)
      接下来的元素就是执行该脚本时传递的参数
      例如: node app.js hello world you are sillyB 执行app.js文件
      那么process.argv数组就是
      ['C:\\Program Files\\nodejs\\node.exe',
       'F:\\NodeJS\\node_demo\\app.js',
       'hello','world','you','are','sillyB']
      
      
    2.process.exit(num) 该指令用来结束当前脚本的执行
      process.exit(0) 指脚本正常执行结束 没有出现异常
      process.exit(1) 指脚本出现的异常 异常退出程序 
      
    
    3.process.env 该值用来判断部署的环境
      在package.json中添加scripts
      "scripts":{
        "dev":"set process.env=development&&node index.js",
        "build":"set process.env=production&&node index.js"
      }  
      后执行npm run dev 就是将环境设置成了开发环境
      后执行npm run build 就是将环境设置成了生产环境
