# v-if和v-else
条件判断是程序中最常见的，在 `Vue.js` ，我们使用 `v-if` 指令实现同样的功能。
```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue条件</title>
</head>
<body>
	<div id="app">
		<p v-if="show">you can see me !</p>
		<button @click="show = !show">Switch</button>
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
				show: false,
			},
		});
	</script>
</body>
</html>
```

有 `v-if` 当然也有 `v-else` 添加一个 “else” 块：

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue条件</title>
</head>
<body>
	<div id="app">
		<p v-if="show">you can see me ! <span>Hello</span></p>
		<p v-else>Hello Vue</p>
		<button @click="show = !show">Switch</button>
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
				show: false,
			},
		});
	</script>
</body>
</html>
```
> if 条件判断时，不管该DOM元素内有多少子元素，都会被一起隐藏掉