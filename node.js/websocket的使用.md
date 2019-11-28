##websocket的使用

1.app.js 

```shell
npm i ws #安装第三方插件ws
```



```js
const WebSocket = require('ws')
const ws = new WebSocket.Server({port:8080})

let clients = []
ws.on('connection',(client)=>{
  //只要有一个客户端与该服务器连接,就会触发该事件,client就是该客户端
  clients.push(client)
  //监听客户端向服务端发送消息
  client.on('message',(msg)=>{
    //msg是客户端向服务器发送的数据
    //判断数据是否符合某一条件然后向客户端发送数据
    clients.foreach(client=>{
      //client.send('字符串')->只能发送字符串数据
      client.send(JSON.stringify({name:'蔡徐坤',age:28}))
    })
  })
  //监听客户端断开连接
  client.on('close',()=>{
    console.log('有一个客户端断开了连接')
  })
})
```

2.index.html

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
</head>
<body>
<script>
  window.onload = () => {
    //创建连接对象
    const ws = new WebSocket('ws://localhost:8080/')
    ws.onopen = () => {
      //客户端向服务端发送数据
      ws.send('Hello World')
    }
    ws.onerror = () => {
      console.log('error~')
    }
    //接受服务端发送的数据
    ws.onmessage = (msg) => {
      //msg是一个对象 msg.data是服务端发送到客户端的消息
      console.log('接收到服务端推送的消息:', msg.data)
      alert(msg.data)
    }
    ws.onclose = () => {
      console.log('closed~')
    }
  }
</script>
</body>
</html>
```



