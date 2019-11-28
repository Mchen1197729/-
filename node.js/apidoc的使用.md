##apidoc用于自动生成接口文档

```js
/**
 * @api {post} /user/register 用户注册
 * @apiName Register
 * @apiGroup User
 *
 * @apiParam {String} username 用户名
 * @apiParam {String} password 用户密码
 *
 * @apiSuccess {Number} code 0
 * @apiSuccess {String} msg  注册成功
 * @apiSuccessExample {json} Success-Response:
 * {
 *   code:0,
 *   msg:'注册成功'
 * }
 *
 * @apiError {Number} code  1
 * @apiError {String} msg  注册失败
 * @apiErrorExample  {json} Success-Response:
 * {
 *   code:1,
 *   msg:'注册失败'
 * }
 */
```

```shell
#在根目录创建文件夹apidoc
#在根目录创建apidoc.json文件,内容是
{
	"name": "注册登录评论", #接口文档的name
  "version": "0.1.0",   #版本
  "description": "注册登录评论接口文档", #接口文档的描述
  "title": "接口文档", #标题
  "url": "http://localhost:3000" #接口的完整请求地址(其他都不重要,就这一个重要)
}
#运行命令 
apidoc -i ./ -o ./apidoc
#会自动在apidoc文件夹中生成很多文件,其中有index.html文件,用浏览器打开即可
```

