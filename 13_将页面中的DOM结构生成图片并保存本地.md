##将页面中指定的DOM结构以图片的形式保存到本地

####相关的库：html2canvas、download.js

####思路：先利用html2canvas将指定的DOM结构生成canvas,再利用download.js将canvas中的内容保存到本地。

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport"
        content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>html2canvas保存到本地</title>
  <style>
    #capture {
      padding: 10px;
      background: #f5da55;
    }

    #capture h4 {
      color: #000;
    }
  </style>
</head>
<body>
<div id="capture">
  <h4>Hello world!</h4>
</div>
<button id="btn">按钮</button>
<script src="./html2canvas.js"></script>
<script src="./download.js"></script>
<script>
  document.getElementById('btn').onclick = function () {
    //将DOM结构生成canvas结构添加到body中
    //DOM结构可以自己指定
    html2canvas(document.querySelector("body")).then(canvas => {
      //保存此canvas到本地
      //生成canvas的dataURL
      let dataURL = canvas.toDataURL();
      download(dataURL, 'html2canvas.png', 'image/png');
    });
  };
</script>
</body>
</html>
```

