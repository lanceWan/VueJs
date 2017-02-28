# Hello Vue
本教程直接独立版本安装，即直接下载并用 `<script>` 标签引入`Vue` ，Vue 会被注册为一个全局变量。至于用 `npm` 、`命令行工具` 等安装方式本教程不做讲解，从最基础的方式讲解 `Vue` ，不掺杂其他技术。

> Vue CDN : [https://unpkg.com/vue@2.1.10/dist/vue.js](https://unpkg.com/vue@2.1.10/dist/vue.js)

```html
<!DOCTYPE html>
<html>
<head>
	<title>安装</title>
</head>
<body>
	<div id="app">
		<h1>{{title}}</h1>
	</div>
 	<script type="text/javascript" src="../js/vue.js"></script>
 	<script type="text/javascript">
 		var app = new Vue({
 			el: '#app',
 			data: {
 				title: 'hello Vue'
 			}
 		});
 	</script>
</body>
</html>
```

* `el`（Vue管理的作用域）
* `data` （属性，相当于后端语言 `MVC` 模式中的 `M`,即数据模型，提供数据） 

> 作用域官方不建议挂载到 `HTML` 的根上