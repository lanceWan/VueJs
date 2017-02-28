# v-else-if
`v-else-if`，顾名思义，用作 `v-if` 的 `else-if` 块。可以链式的多次使用，在 Vue 2.10 版本中新增。
```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue条件</title>
</head>
<body>
	<div id="app">
		<div v-if="type === 'A'">
			A
		</div>
		<div v-else-if="type === 'B'">
			B
		</div>
		<div v-else-if="type === 'C'">
			C
		</div>
		<div v-else>
			Not A/B/C
		</div>
		<hr>
		<input type="text" v-model="type">
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
                type: 'A',
			},
		});
	</script>
</body>
</html>
```