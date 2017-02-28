# 绑定style数组形式
`v-bind:style` 的数组语法可以将多个样式对象应用到一个元素上。

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
		<div class="demo" :style="[myStyle,{height: width + 'px'}]"></div>
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

> 当 v-bind:style 使用需要特定前缀的 CSS 属性时，如 transform ，Vue.js 会自动侦测并添加相应的前缀。