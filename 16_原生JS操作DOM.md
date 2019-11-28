## 原生js操作DOM 

```html
<ul id="fruits">
  <li class="item one">Apple</li>
  <li class="item two">Banana</li>
  <li class="item three">Pear</li>
</ul>
<script>
  //ulNode是DOMElement类型的变量
	let ulNode = document.getElementById('fruits');
  
  console.log(ulNode.innerHTML); 
  //带有格式的字符串：
  /*
  `
  <li class="item one">Apple</li>
  <li class="item two">Banana</li>
  <li class="item three">Pear</li>
  `
  */
  //属性
  //childNodes属性会将文本节点遍历出来,数组中每个元素都是DOMElement类型的变量
  let childs = ulNode.childNodes; //[text,li,text,li,text,li,text]
  
  //children属性只不会将文本节点遍历出来,数组中每个元素都是DOMElement类型的变量
  let children = ulNode.children; //[li,li,li]
  
  //遍历子元素
  for(let i=0;i<children.length;i++){
    //伪数组：{0:'item',1:'one',value:'item one',length:2}
    console.log(children[i].classList); 
  }
</script>
```

```html
<ul id="fruit">
  <li class="item one">Apple</li>
  <li class="item two">Banana</li>
  <li class="item three">Pear</li>
</ul>
<hr/>
<div id="box"></div>
<script>
  //克隆节点
  //node.cloneNode(true/false) 返回被克隆的节点
	//参数默认是true,表示深度克隆
	/*
	克隆一个元素节点会拷贝它所有的属性以及属性值,当然也就包括了属性上绑定的事件,
	但不会拷贝那些使用addEventListener()方法或者node.onclick = fn这种用JavaScript动态绑定的事件.
	*/
  let ul = document.getElementById('fruit');
  let div = document.getElementById('box');
  console.log(ul);
  console.log(div);
  //克隆节点
  let ulCopy = ul.cloneNode(true);
  //将id值修改掉，避免出现两个相同id的元素
  ulCopy.setAttribute('id', 'fruit-copy');
  console.log(ulCopy);
  div.appendChild(ulCopy);
</script>
```

