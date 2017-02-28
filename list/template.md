# Template v-for
如同 `v-if` 模板，你也可以用带有` v-for` 的 `<template>` 标签来渲染多个元素块。
```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue条件</title>
</head>
<body>
	<div id="app">
		<template v-for="(fruit,index) in fruits">
			<h1>{{fruit}}({{index}})</h1>
			<hr>
		</template>
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
                fruits:['香蕉','苹果','芒果','火龙果'],
				website:[
					{name: '百度' , url: 'http://www.baidu.com'},
					{name: '晚黎' , url: 'http://www.iwanli.me'},
					{name: 'Google' , url: 'http://www.google.com'},
				]
			},
		});
	</script>
</body>
</html>
```