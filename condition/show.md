# v-show
另一个根据条件展示元素的选项是 `v-show` 指令。用法大体上和 `v-if` 一样。
```html
<!DOCTYPE html>
<html>
<head>
	<title>Vue条件</title>
</head>
<body>
	<div id="app">
		<p v-if="show">you can see me ! <span>Hello</span></p>
		<p v-show="show">Hello Vue</p>
		<button @click="show = !show">Switch</button>
	</div>
	<script type="text/javascript" src="../js/vue.js"></script>
	<script type="text/javascript">
		var app = new Vue({
			el: '#app',
			data: {
				show: true,
			},
		});
	</script>
</body>
</html>
```

## v-if VS v-show
`v-if` 是真实的条件渲染，因为它会确保条件块在切换当中适当地销毁与重建条件块内的事件监听器和子组件。
`v-if` 也是惰性的：如果在初始渲染时条件为假，则什么也不做——在条件第一次变为真时才开始局部编译（编译会被缓存起来）。
相比之下，` v-show` 简单得多——元素始终被编译并保留，只是简单地基于 CSS 切换。

## v-if 和 v-show 怎么选择 ?
一般来说，` v-if` 有更高的切换消耗而 `v-show` 有更高的初始渲染消耗。因此，如果需要频繁切换使用 `v-show` 较好，如果在运行时条件不大可能改变则使用 `v-if` 较好。