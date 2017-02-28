# template中v-if条件组
因为 `v-if` 是一个指令，需要将它添加到一个元素上。但是如果我们想切换多个元素呢？此时我们可以把一个 `<template>` 元素当做包装元素，并在上面使用` v-if`，最终的渲染结果不会包含它。
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
		<template v-if="show">
			<h1>title</h1>
			<p>template 模块组</p>
		</template>
		<template v-else>
			<h1>title</h1>
			<p>template 模块组1111</p>
		</template>
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
>  `<template>` 元素当做包装元素，最终不会再浏览器中渲染出来