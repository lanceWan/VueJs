# 绑定style对象形式
`v-bind:style` 的对象语法十分直观——看着非常像 `CSS` ，其实它是一个 `JavaScript` 对象。 `CSS` 属性名可以用驼峰式（camelCase）或短横分隔命名（kebab-case）：

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue绑定class</title>
	<style>
		.demo{
			width: 100px;
			height: 100px;
			background-color: gray;
			display: inline-block;
			margin: 20px;
		}
	</style>
</head>
<body>
	<div id="app">
		<div class="demo" :style="{backgroundColor: color}"></div>
		<div class="demo"></div>
		<div class="demo"></div>
		<hr>
		<input type="text" v-model="color">
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
				color: 'pink'
			}
		});
	</script>
</body>
</html>
```

> 在 CSS 样式中 `backgroud-color` 是以短横分隔命名，在 Vue 中统一用驼峰式，即 `backgroundColor`

同样的，对象语法可以结合返回对象的计算属性使用。

```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue绑定class</title>
	<style>
		.demo{
			width: 100px;
			height: 100px;
			background-color: gray;
			display: inline-block;
			margin: 20px;
		}
	</style>
</head>
<body>
	<div id="app">
		<div class="demo" :style="{backgroundColor: color}"></div>
		<div class="demo" :style="myStyle"></div>
		<div class="demo"></div>
		<hr>
		<input type="text" v-model="color">
		<input type="text" v-model="width">
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
				color: 'pink',
                width: 100,
			},
			computed: {
			    myStyle(){
			        return {
                        backgroundColor: this.color,
						width: this.width  + 'px'
					}
				}
			}
		});
	</script>
</body>
</html>
```