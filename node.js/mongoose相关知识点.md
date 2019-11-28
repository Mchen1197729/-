##mongoose的使用

```js
const mongoose = require('mongoose')

//连接数据库 数据库名:blog
mongoose.connect('mongodb://localhost/blog', {useNewUrlParser: true})

//获取连接对象
const conn = mongoose.connection

//监听连接状态
conn.on('connected', () => {
  console.log('db connect success')
})

//获取Schema对象
const userSchema = new mongoose.Schema({
  //存进mongodb数据库的数据会自动产生一个_id的主键
  username: {type: String, required: true}, //字段的属性描述
  password: {type: String, required: true},
  age: {type: Number, min: 0, max: 120},
  sex: {type: Number, default: 0}
}, {versionKey: false}) //在增加数据时,不产生__v(关于版本信息)这个字段

//获取对应的Model
const UserModel = mongoose.model('user', userSchema) //->对应的表名为:users

module.exports = UserModel
```

